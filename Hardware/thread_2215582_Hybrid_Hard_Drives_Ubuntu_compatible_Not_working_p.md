---
title: "Hybrid Hard Drives Ubuntu compatible? Not working properly with mine."
date: 2014-04-07
forum: Hardware
---

### Post by Heeter on 2014-04-07
Hi all,

I just purchased a Seagate 1TB SSHD hard disc for my laptop. I previously had a 250GIG with Ubuntu installed and working fine on this laptop, but it was full.

Anyways, I have tried a few times to reinstall 13.10 64bit from a fresh install onto this new drive, and after a reboot or 2, I get a grub command screen show up.

Are these Hybrid drives incompatible with Ubuntu, or can I try something else?

Thanks

Heeter

---

### Post by Kirboosy on 2014-04-07
What kind of partition setup are you using on your drive? Are you having the system install to the SSD portion and the home partition on the regular spindle portion?


Hope that helps!
~Caboose

---

### Post by Heeter on 2014-04-07
Thanks Caboose885,

I am using the default install setup,

According to seagate, the install should be just like a regular HD. In the BIOS, all 1TB is recognized as one, single HD.

Heeter

---

### Post by Kirboosy on 2014-04-07
You said that after a reboot or two it presents you with a GRUB prompt. Are you installing all available updates during this time? I'm currious if an update to grub or readahead could be wreaking havoc on the sytem.

~Caboose

---

### Post by Heeter on 2014-04-07
Yes, I am.

I do download updates while installing, and as well install third party plugins

Thanks

Heeter

---

### Post by Bashing-om on 2014-04-07
Heeter; Hello,

Recently I too have been going 'round and 'round with Grub, I have learned a thing or three new. Maybe I can help.

1. OK, you mention a 250 Gig original drive, is this drive still a part of the equation ? .. and what release is installed onto this original drive (if it is still a part of the equation) -Grub 2.0 and Grub 1.99 do not always play nice together when grub 2.0 tries to parse 1.99 files for the boot menu ! 

2. Do you now boot to a grub menu ( grub >) ? If so we need to know what the operating system thinks it sees;

from that grub prompt are positive results obtained from ?:
- For a standard install, where '/' (root) is installed to sda1 -
```

ls (hd0,msdos1)/boot/grub/grub.cfg
ls (hd0,msdos1)/vmlinuz
ls (hd0,msdos1)/
ls /initrd.img

```

3. If all the above results are positive, let's see if you can boot, and we fix grub later.
From the grub prompt:
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1
initrd (hd0,msdos1)/initrd.img
boot

``` Hopefully you boot the operating system.

4. If you are attempting to dual boot, and can not boot from Grub prompt, going to have to look at the file '/boot/grub/grub.cfg' next and see if we can determine what is not going on, or what is that should not be. Then, well, getting too far ahead of myself. Let's see what results from the aboves.

I would prefer to take this approach, rather then a possible quick fix by several methods to (RE-)install grub ( just to have it messed up again in 3 or 4 boots).

That is my thoughts, whatever yall (Caboose885) want to do.

[INDENT][INDENT]I am in the game
[/INDENT][/INDENT]

---

### Post by Heeter on 2014-04-07
Awesome, thanks for sticking with me.......

1 - the 250GIG has been completely removed and totally out of the equation. I am only dealing with the 1TB Hybrid here in this laptop.

2 - the first set of commands shows up no errors.

3 - the first command line in grub shows up as:
```

grub> linux (hd0,msdos1) /vmlinuz root=/dev/sda1
error: invalid file name ' '.

```

I have not tried the next commands after this one.

4 - There will be no dual booting, just 13.10 64bit.

Heeter

---

### Post by Bashing-om on 2014-04-07
Heeter; Hey, 

regret the delay in getting back, busy busy forum.
A small thing -> means a lot .. that little bitty space.
Try again:
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1
initrd (hd0,msdos1)/initrd.img
boot

```
and be advised there is no space between 'msdos1)' and '/vmlinuz'.
If at all possible, for best results copy and paste commands and outputs back to the post. And hey I too make my share of errors, as much as I try to watch out for those "little things".

[INDENT][INDENT]we will all plow 
[INDENT][INDENT][INDENT]through this too together 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Heeter on 2014-04-07
LOL

I was putting that space in there.....

Well, I have now made it onto my desktop.....

Now what can I do to repair grub?

Thanks!

Heeter

---

### Post by Bashing-om on 2014-04-07
Heeter; Great !

I did not anticipate it really being that effective ( thought one of the control files would be messed up) .....
OK, as you can boot to the desktop through grub, that tells us that all the mechanisms are in place, and most/(all?) of the control files are intact.
May I suggest though that just as a precaution we take a gander at grub's menu control file and see what the system has built ?..
```

cat /boot/grub/grub.cfg

```

Then run terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo update-grub

```
to regenerate and rebuild some of grub's control files.

reboot and lets see that grub now takes care of booting the operating system.

[INDENT][INDENT]ain't nothing now
[INDENT][INDENT][INDENT]but a thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Heeter on 2014-04-07
Great, now it it is booting into the desktop.

But the grub menu is now showing up at the beginning of boot.

Can I get rid of it and boot straight into desktop?

Thanks a million for helping out, Bashing-om

Heeter

---

### Post by Bashing-om on 2014-04-07
Heeter; Well, Well.

That one gets a boot menu with only one operating system installed is;
a) a value set in the control file '/etc/default/grub' .
b) The result of a failed last boot attempt,
c) A failure in a control file.

Let's take the simpler & most likely cause and look at:
```

cat /etc/default/grub

```

see what that control file has set.

[INDENT][INDENT]we be steppn'  now
[/INDENT][/INDENT]

---

### Post by Heeter on 2014-04-07
```

adminpc@adminpc:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
adminpc@adminpc:~$ 

```


Heeter

---

### Post by Bashing-om on 2014-04-07
Heeter;

Presently -under the new changes to grub - I am not absolutely sure, but let's try:
```

sudo cp /etc/default/grub /etc/default/grub-07apr2014 ##just so we have a fallback !##
gksudo gedit /etc/default/grub

```
change:
'GRUB_TIMEOUT=10'
to
'GRUB_TIMEOUT=0'
Save the file and exit back to the desk top.
Once more propagate the change:
```

sudo update-grub

``` for that change to take effect.

Reboot - I will not be surprised to see the boot menu at this time ( change in grub) , select ubuntu, and reboot.

Now I expect you to boot straight to the operating system without a grub menu display.

---

### Post by Heeter on 2014-04-07
Awesome, Thanks for  all your help

The grub screen is gone.


Heeter

---

### Post by Bashing-om on 2014-04-07
Heeter; Great !

You do good work.

As this situation is concluded, please mark this thread solved, aids others seeking a similar solution, and as well helps keep the forum tidy; thread tools @ top of post.

[INDENT][INDENT]let the good times
[INDENT][INDENT][INDENT]roll on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Heeter on 2014-04-07
Will Do, Thanks again

Heeter

---

