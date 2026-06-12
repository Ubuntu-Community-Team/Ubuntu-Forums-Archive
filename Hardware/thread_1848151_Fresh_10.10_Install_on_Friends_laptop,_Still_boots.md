---
title: "Fresh 10.10 Install on Friends laptop, Still boots to grub?"
date: 2011-09-22
forum: Hardware
---

### Post by Rasa1111 on 2011-09-22
Hey all, 

I've run into something I've only seen once before , I think.- and dont know why it happens or how to fix it. 

I just did a fresh install on this Compaq laptop,
Installed 10.10 over win7, So only ubuntu on the disk now. 

when Ive got it running, it runs great!  no surprise there...
but whenever it's rebooted, it always boots to the grub screen, which I [she] will have no use for. It doesnt need to be seen, anyway.

Is there a way to make it so that this boots straight into the OS, without giving me the GRUB screen first? 

Also..
It seems that when it's rebooted, every... say- 1 in 3 times,
it will give me the grub screen,  I will select the OS, and it will begin to boot, 
then it just hangs on a black screen with a flashing cursor.

and it sits like this until i hit a key, 
with which it replies..
(something like) "Root device mount timed out"-"intramfs....."
does that sound familair? Lol! Sorry..
Ill have to look closer when it happens again. 

I'm wondering if i didnt need to go through the grub screen, if the same errors would occur? or would it just boot right into the system? lol
hmm..

Anyone got any ideas? 
Thanks in advance!

---

### Post by ibutho on 2011-09-22
If you do not want to see the grub screen, edit /boot/grub/menu.lst or /etc/default/grub depending on your distro and change the timeout from 10 to 0. I am not sure about the hang when you reboot.

---

### Post by Rasa1111 on 2011-09-22
Hey thanks, I'll give it a try. 

I learned a little more..

So..
Whenever I do a reboot now, it reboots, and then hangs at the black screen w/flashing cursor..
then I hit a key, (usually H key i guess) lol
and it gives me the " gave up waiting for root mount device" [er somthin]
and the [initramfs] 

so at [initramfs] i type *exit* and it boots into the system like normal.

what the heck is that about? lol

Thanks ibutho, I'll see what happens with that. :)

---

### Post by Rasa1111 on 2011-09-22
ok, sorry it's gotta be this way, but this is the only way I could get a shot. lol
]
Got the Grub timeout changed from 10 to 0. Thanks again!

Now,
Still, on a reboot...
I get the black screen/cursor..
and i hit enter..

and the screen you see appears.

Then, where it  says (initramfs)
I have to type *exit*, then hit enter, then hit spacebar!
THEN it boots into the system. :lol: lol

I dunno what's up with this. :???:

---

### Post by ibutho on 2011-09-22
Have you upgraded the kernel on this system?

---

### Post by Rasa1111 on 2011-09-22
I've not done anything [system wise] but install 10.10 Fresh, and then apply the needed updates. 
300+ MB's worth. 

This is the kernel info..
[ATTACH]202687[/ATTACH]
prob not what ya need.., I don't know! ??? lol

---

### Post by technosysind on 2011-09-22
I think you need fresh installation. In case you are making a dual boot, install using wubi

---

### Post by Rasa1111 on 2011-09-22
hmm..
i just installed it! lol
:/
No dual boot.
only Ubuntu , as stated above. 

ill probably end up trying a reinstall though if i don't get it.
see if that helps, i dunno. 
grr.

---

### Post by Rasa1111 on 2011-09-22
ANyone got any more ideas?
before I actually go through a whole new install again, and get it all setup and customized all over again? 

I don't mind the installs soo much,
just all the updates after, and having to spend the time getting it customized to be easy to use for a windows person. :???: lol

hmmm

---

### Post by technosysind on 2011-09-22
Go for it. I really don't think that there is any better option.

---

### Post by Rasa1111 on 2011-09-22
I just hate to do all that, all over again..
only to find it does the same damn thing! :/ lol

---

### Post by ibutho on 2011-09-22
How many kernels are listed in your grub config file or the grub boot menu? I suspect that you may have upgraded to a kernel thats not playing nice with your hardware.

---

### Post by Rasa1111 on 2011-09-22
> **ibutho said:**
> How many kernels are listed in your grub config file or the grub boot menu? I suspect that you may have upgraded to a kernel thats not playing nice with your hardware.

hey ibutho,
here is what my grub file says...
is this the right file?
from /etc/default/grub

```
If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```
if it's something else I need, let me know, thank you!

---

### Post by ibutho on 2011-09-22
The info I need to look at is in /boot/grub/grub.cfg, so post the output of
```
cat /boot/grub/grub.cfg
```

---

### Post by Rasa1111 on 2011-09-22
ohh alright, thank you.

  Here it is.
edit: crap, took it from the wrong laptop. :lolflag:
brb

Ok, here it is.

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 93722094-d374-43f7-828a-bf6c4af6a883
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 93722094-d374-43f7-828a-bf6c4af6a883
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 93722094-d374-43f7-828a-bf6c4af6a883
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=93722094-d374-43f7-828a-bf6c4af6a883 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 93722094-d374-43f7-828a-bf6c4af6a883
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=93722094-d374-43f7-828a-bf6c4af6a883 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 93722094-d374-43f7-828a-bf6c4af6a883
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=93722094-d374-43f7-828a-bf6c4af6a883 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 93722094-d374-43f7-828a-bf6c4af6a883
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=93722094-d374-43f7-828a-bf6c4af6a883 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 93722094-d374-43f7-828a-bf6c4af6a883
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 93722094-d374-43f7-828a-bf6c4af6a883
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```

:confused:

---

### Post by ibutho on 2011-09-22
It appears that you have two different kernels installed. I suggest changing the grub timeout back to 10, booting from the older kernel (Linux 2.6.35-22-generic) and see if you have the same problems when you reboot (Each time you reboot, select Linux 2.6.35-22-generic). If the old kernel works better than the new one (Linux 2.6.35-30-generic), it might be best to use that as default.

---

### Post by Rasa1111 on 2011-09-22
Progress! lol

Thank you man. :)

Ok, As you said..
I selected the old kernel, and it booted right up. 

Is there anyway to make it just boot into that kernel by default?
or
is there a way to remove the one that's not working?

also..
how the hell did I get 2 kernels? lol

Many thanks for your time.
I appreciate it.

---

### Post by maul9999 on 2011-09-22
> **Rasa1111 said:**
> Hey all, 

I've run into something I've only seen once before , I think.- and dont know why it happens or how to fix it. 

I just did a fresh install on this Compaq laptop,
Installed 10.10 over win7, So only ubuntu on the disk now. 

when Ive got it running, it runs great!  no surprise there...
but whenever it's rebooted, it always boots to the grub screen, which I [she] will have no use for. It doesnt need to be seen, anyway.

Is there a way to make it so that this boots straight into the OS, without giving me the GRUB screen first? 

Also..
It seems that when it's rebooted, every... say- 1 in 3 times,
it will give me the grub screen,  I will select the OS, and it will begin to boot, 
then it just hangs on a black screen with a flashing cursor.

and it sits like this until i hit a key, 
with which it replies..
(something like) "Root device mount timed out"-"intramfs....."
does that sound familair? Lol! Sorry..
Ill have to look closer when it happens again. 

I'm wondering if i didnt need to go through the grub screen, if the same errors would occur? or would it just boot right into the system? lol
hmm..

Anyone got any ideas? 
Thanks in advance!

It can be your friend's laptop hardware issued.  Check it with windows 7 if you have one.

---

### Post by Rasa1111 on 2011-09-22
I just need to know how to remove the 2nd kernel, or at least remove it from GRUB.

---

### Post by Rasa1111 on 2011-09-22
Woohoo! I fixed it!!  Yes!  lol :D 

I just removed the kernel i didnt need , using synaptic, 
updated grub, rebooted, and it booted directly into the OS! 
[B]
ibutho[/B]! Thanks soo much man!
wouldnt have gotten this without you. :)
You rock! :guitar: <3

---

### Post by ibutho on 2011-09-22
> **Rasa1111 said:**
> Woohoo! I fixed it!!  Yes!  lol :D 

I just removed the kernel i didnt need , using synaptic, 
updated grub, rebooted, and it booted directly into the OS! 
[B]
ibutho[/B]! Thanks soo much man!
wouldnt have gotten this without you. :)
You rock! :guitar: <3

No worries. I'm glad I managed to help and the system is working as it should.

---

### Post by Rasa1111 on 2011-09-23
Big time help! 
*deep bows*

now, all she needs is a new keyboard and this thing would be like new! lol :P 

where can i get the PPA for that? 
[I]sudo add-apt-repository ppa:new-keyboard
sudo apt-get update
sudo apt-get install new keyboard.[/I]
 :lol: 

This community is awesome. <3
thanks again

---

