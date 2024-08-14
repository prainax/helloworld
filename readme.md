# hello world

A small bootloader that will print Hello World on screen. We will use a floppy for booting (I know you dont want to crash your harddrive for this). We will use normal 3.5 inch floppy for this.

```bash
mkdir bin

# Create a blank floppy image.
dd if=/dev/zero of=bin/drive.img bs=512 count=2880 status=none

# Assemble and copy the bootloader.
nasm bootloader.asm -f bin -o bin/boot.bin
dd if=bin/boot.bin of=bin/drive.img bs=512 count=1 conv=notrunc status=none

# Launch the emulator.
qemu-system-x86_64 -drive file=bin/drive.img,index=0,if=floppy,format=raw -boot a
# bochs -f bochs_config.txt -q

```


# Disclaimer
Please read all the instruction carefully and then try. Dont use your hard disk for booting your bootloader.
