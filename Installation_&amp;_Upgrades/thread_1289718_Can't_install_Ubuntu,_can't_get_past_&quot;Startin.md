---
title: "Can't install Ubuntu, can't get past &quot;Starting Init crypto disks...&quot;"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by Tanchistu on 2009-10-12
Hello,

I'm trying to install Ubuntu 9.10 and I get this errors:

[IMG]http://i998.photobucket.com/albums/af103/Tanchistu/1.jpg[/IMG]

after this the monitor goes to sleep and nothing happens.

I thought that the errors are caused by some of the hardware so I have unplugged all of my HDDs, but one. I don't have the errors:

[IMG]http://i998.photobucket.com/albums/af103/Tanchistu/2.jpg[/IMG]

... but the monitor still goes to sleep.

I have also took off the TV tuner with no effect. I don't think I can take out any other piece of hardware and still have a functional PC.

I have tried normal install and live install, the same problem. As I remember I have the same problem with older versions of Ubuntu, but without anything on the screen, just a black monitor.

Thank you.

---

### Post by Tanchistu on 2009-10-13
Sorry for bumping my own thread, but this issue is keeping me from using Ubuntu.

I think that it's an hardware issue, no you think that I should replace my video card?

---

### Post by patrickjlbyrne on 2009-10-13
me too!

trying to boot ubuntu netbook remix beta 1

a usb image made from the latest daily build seems to boot to the live desktop ok. installing now (touch wood).

---

### Post by Tanchistu on 2009-10-14
I have replaced the video card, it seems that this was the problem, I consider it a bug.

If you need more info, I would happily help.

BR.

---

### Post by khurtsiya on 2009-11-10
Same problem with installation from flash on Lenovo ThinkPad SL500.

Any solutions or tips yet?

Thanks!

---

### Post by bltblt on 2009-11-18
bump...

I have the same symptom, but with a slightly different configuration.

I'm able to boot using a LiveCD. 'Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)'

When I create the LiveUSB using LiveUSBcreator in Ubuntu that is booted from the LiveCD **or** UNetbootin from the same LiveCD iso, it won't boot the PC, but hangs as follows:

[INDENT]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$  * Starting init crypto disks...              [ OK ]
[/INDENT]

At the top of the screen, I see this message:
[INDENT]Use of uninitialized value $item in hash element at /usr/share/perl5/Debconf/DbDriver/File.pm line 70, <$__ANONIO__> chunk 1.
[/INDENT]

Any ideas for troubleshooting or further diagnostics appreciated.

thanks!

---

### Post by johanster on 2009-12-07
I had the same problem as described above, the system stopping at "Starting init crypto disks". 

For me it was enough to start in recovery mode (press esq in grub), then selecting "resume" in the recovery menu, logging into a shell then just rebooting the machine. The next normal boot worked as expected. Not sure exactly what the recovery mode boot did differently though.

---

### Post by yknott on 2010-01-23
had the same issue while attempting to boot into kubuntu 9.10 live through a usb stick

tried the live dvd as well, no change

and removed 'quiet' but nothing else shown on the screen seemed relevant



poked around in bios, 

eventually disabled "UDMA" to IDE drives

booting into kubuntu live from the usb stick worked after this

system: dell dimension 4800

---

### Post by dfaure on 2010-03-25
I was having the same problem when trying to install kubuntu 9.10 on a Dell Latitude E4300 laptop. My solution was: download and burn the 10.04 beta1 to a CD, install from that CD.

Then I hit bug 526486 and had to start the installer by hand (ubiquity kde_ui), but that's another story.

---

