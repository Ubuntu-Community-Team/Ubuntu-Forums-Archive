---
title: "apci  problomes with 10.04 on toshiba satellite C650D"
date: 2010-08-16
forum: Hardware
---

### Post by killernat on 2010-08-16
im turning this into an install guide

Unadresed problems:
1. battery not detected / no power mangement
2. boot splash screen

booting from the live cd:
after inserting the disk and booting when the you get to the purple splash screen press "esc" select your language then press F6 and select "no=acpi"

install as you normally would if you are new to Linux here is a [guide]("http://techie-buzz.com/foss/ubuntu-10-04-lts-installation-guide.html")

when you reboot at the grub menu press 'e' on the first item of the list this will bring you to a bunch of commands 
> Move to the line:
> linux /vmlinuz... ro quiet splash
add options to the end of the line; for example:
> linux /vmlinuz... ro quiet splash apci=off

Type <Ctrl>-x <Enter>

this should get you into ubuntu
after you boot in do this:
> 
open your terminal
and type:  
$ cd /etc/default
$ sudo gedit grub

Change the line:
> GRUB_CMDLINE_LINUX=""
to:
> GRUB_CMDLINE_LINUX="acpi=ht"
quotes required.

save as "/etc/default/grub"

Update the GRUB2 bootloader:
$ sudo update-grub

reboot
to get your sound working right:
next fallow [these instructions]("http://ubuntuforums.org/showpost.php?p=9459478&postcount=38") 
and now [these]("http://monespaceperso.org/blog-en/20...id-lynx-10-04/")

so far this is all i have credit goes to:
spiderman05 and hwbii

original post:

i installed 10.04  but did not know how to have the apci=off option like i had in the live cd i assumed (incorrectly) that the option continued on to the installation can any one tell me how to set apci=off before during or preferably after
i have searched around for a while but am not able to find anything that helped

---

### Post by spiderman05 on 2010-08-17
I have been struggling with my newly purchased Toshiba C650D as well. In order to disable acpi, hit ESC key when the purple screen shows up, then F6, then select acpi=off from the popup menu.

Your wireless card be detected and running out of the box. Though, you will need to download a new release of atl1c module to make your AR8152 ethernet card work. Also, the headphones will not work out of the box, there is a workaround. Finally, you will need to make space for Ubuntu if you want to install it on your hard drive. Toshiba uses all the 4 primary partitions on the HD. I shrank partition 2 to 80GB, then deleted partition 3 and installed ubuntu on the new  primary partition.

This is the post that helped set my ethernet card: [http://ubuntuforums.org/showthread.php?p=9449490](http://ubuntuforums.org/showthread.php?p=9449490)

PS. Disabling ACPI slowed down my computer, there seems to be a kernel upgarade that solves this problem. I am trying this route instead.

Good luck.

---

### Post by hwbiii on 2010-08-17
The GRUB2 bootloader uses scripts to build the boot menu.
If you edit the menu entry in "/grub/grub.cfg" your changes will be lost after the next 
kernel upgrade. A permanent solution is to edit "/etc/default/grub".

$ cd /etc/default
$ sudo {your editor } grub

Change the line:
> GRUB_CMDLINE_LINUX=""
to:
> GRUB_CMDLINE_LINUX="acpi=off"
quotes required.

save as "/etc/default/grub"

Update the GRUB2 bootloader:
$ sudo update-grub

reboot

If you want to interactively make changes to the boot options for testing
purposes, you can edit the menu options on-the-fly. 

When the splash screen displays, immediately press <Shift> (I believe). 
Then the boot menu should display.
Use the up/down arrows to select the desired menu entry (usually the first). 

Press e  . 
Move to the line:
> linux  /vmlinuz... ro
add options to the end of the line; for example:
> linux  /vmlinuz... ro acpi=off

Type <Ctrl>-x <Enter>


Here are a few links to some good documents describing how GRUB2 works & how to set options. You may find that you can partially disable ACPI & still shut down automatically with ACPI. It's worth a try.

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202")

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by killernat on 2010-08-17
> **hwbiii said:**
> The GRUB2 bootloader uses scripts to build 

If you want to interactively make changes to the boot options for testing
purposes, you can edit the menu options on-the-fly. 

When the splash screen displays, immediately press <Shift> (I believe). 
Then the boot menu should display.
Use the up/down arrows to select the desired menu entry (usually the first). 

Press e  . 
Move to the line:
> linux  /vmlinuz... ro
add options to the end of the line; for example:
> linux  /vmlinuz... ro acpi=off

Type <Ctrl>-x <Enter>


[/URL]


ive tried this already but when i boot it still goes to the screen with all the acpi errors
i have also tried to edit the grub file(on a live cd) when i use "sudo update-grub2" it gives me a grub probe error with /dev cannot be found or something like that is there a special way i need to do it  from live cd
this wouldn't be as much of a problem if grub still used menu.lst
edit: ok i got into Ubuntu  i just didnt add the acpi=off at the right spot  so now i should be able to get update grub to load to work

spiderman05 if you read my post i was able to install it meaning i got passed the initial problem with the live cd


edit ok i got it working right thanks for your help now time to figure out what else Ubuntu doesn't like about Toshiba lol

---

### Post by killernat on 2010-08-17
@ spider
actualy toshiba only needs the first 2 so i dumped the last 2 and shrank the 2nd by about 60gb so i have 100 gb for ubuntu thanks for the ethernet fix what was the workaround for the headphones?

---

### Post by spiderman05 on 2010-08-17
> **killernat said:**
> @ spider
actualy toshiba only needs the first 2 so i dumped the last 2 and shrank the 2nd by about 60gb so i have 100 gb for ubuntu thanks for the ethernet fix what was the workaround for the headphones?

Killernat,

OK, I did not know that you already installed Ubuntu. B.t.w, re. option "acpi=off" somebody posted that this will cause the system restrict to a single CPU. He suggested to use "acpi=ht" instead. I am using acpi=ht in my GRUB configuration, this works fine and I can see that both CPUs are being used. I did not check if setting acpi to off will actually cause the system to restrict to one core.

Re. the HD partitions, I read that the 4th partition is the Toshiba recovery partition. I made recovery DVDs when I got my laptop. I will remove this partition as well when I have a chance to check that my recovery DVDs are OK.

The workaround that I tried for the headphones was to add line

options snd-hda-intel model=lenovo

to file /etc/modprobe.d/alsa-base.conf

This solution, worked on Karmik, though I have just noticed that it does not work on Lucent. Now, I have sound coming from both the laptop speakers and the headphones. Also, the mic does not work. I tried values toshiba and acer for model, without any success. This is not a crtical issue for me. I am happy with my configuration so far. I have been a Mandriva user for the past 8 years and I am glad that I finally made the jump to Ubuntu. Mandriva 2010 spring did not boot on my C650D, no errors given, it just freezes :)

---

### Post by spiderman05 on 2010-08-17
After a few hours reading forums, I finally got the headphones and the microphone  to work. The sound card is an Conexant CX20585 chip, per Gnome Alsa Mixer. [saiganeshb]("http://ubuntuforums.org/member.php?u=1085690") found a site that provides drivers for these cards [http://ubuntuforums.org/showpost.php?p=9459478&postcount=38](http://ubuntuforums.org/showpost.php?p=9459478&postcount=38)

You need to make sure, that you also have the C compiler, make utility and header files. Personally, I first upgraded my Alsa driver to 1.0.23 following these instructions [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/) , then I installed the Conexant driver and rebooted.

The C650D laptop is new, so all these headaches to install Ubuntu are somewhat expectable.

---

### Post by yagolf on 2010-08-23
> **spiderman05 said:**
> 
You need to make sure, that you also have the C compiler, make utility and header files. Personally, I first upgraded my Alsa driver to 1.0.23 following these instructions [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/) , then I installed the Conexant driver and rebooted.



This doesn't work for me. I already have ALSA 1.0.23 and installed the alsa-driver-linuxant_1.0.23.0_all.deb, but there was no change in my system after rebooting, my headphones still don't work... Anybody has more ideas?

Re the problem with the acpi, I have solved it installing kernel 2.6.35 and adding "acpi=copy_dsdt", as recommended [in this bug report]("https://bugs.launchpad.net/ubuntu/+bug/612341")
I have also tried "acpi=ht" and it gives me functionality for both processors as well. As I am quite new to the linux world, I don't know which one's best, but I just thought I'd mention it, I'm sure it'll help someone.

I have another problem that may not belong to this thread but given the fact that we're all concerned with the same machine, I'm going to throw it in and if anybody can point me in the right direction, the more the merrier:
As you all probably know, the Synaptics Touchpad on this laptop supports multitouch and it works fine on Windows but I can't make it work in Lucid. I've tried with gsynaptics and with gpointing-device-settings but none give me the functionality I was expecting.

I really want to have this machine working at its fullest for it is a good computer with a very nice design and running into so many little things is burning me down...:mad:
As I said before, any help would be much appreciated.

:guitar: rock on

---

### Post by orthopod on 2010-08-26
try a fresh install with 10.10 alpha-3 Maverick .  everything works perfectly - battery, cpu scaling, wireless, fans, all cores recognized.
no arguments have to passed to  grub either

i tried updating from 10.04, and that didnt work, but the fresh install did.

---

### Post by killernat on 2010-08-29
> **orthopod said:**
> try a fresh install with 10.10 alpha-3 Maverick .  everything works perfectly - battery, cpu scaling, wireless, fans, all cores recognized.
no arguments have to passed to  grub either

i tried updating from 10.04, and that didnt work, but the fresh install did.
ill  make a new partition and  try that

---

### Post by rabidchicken on 2010-08-31
Thanks for the guide. I just installed ubuntu for my sister on her toshiba c650d, once i found this it basically answered all of my questions.

---

### Post by killernat on 2010-08-31
so i tried 10.10 &#945;3 but it has the same acpi problomes

---

### Post by yossman on 2010-09-24
hi guys, been working for the last couple days to get a toshiba satellite C650D laptop working on ubuntu 10.04 as well.  this thread was very helpful in hinting on how to get ACPI support and sound system working properly, but current summary in first post didn't quite work out for me.  

i tried to get ubuntu 10.10 beta (2010-09-02) installed but none of the USB key install attempts i did would work (i386 or AMD 64, both halted before loading kernel, even with different USB install key creators), and i didn't have a CDR handy to try CDROM boot route.

my point form troubleshoot list to get this working on ubuntu 10.04 follows:

- base ubuntu 10.04 system doesn't support ACPI or sound system properly. the system hangs on boot.  you can add 'acpi=off' to the kernel boot line on the liveCD or USB key installer to get ubuntu loaded at least.

- upgraded to linux kernel 2.6.35-rc1 
(linux-source-2.6.35_2.6.35-020635rc1) which i got as a .deb from:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/)
(i grabbed the i386 packages, used dpkg -i to install them)

- added 'acpi=copy_dsdt' to kernel boot line in /etc/default/grub. reboot.

- this enabled my power management and ethernet network card! yay..

- sound system is still sketchy;
- internal speakers work but headphone jack is busted
- tried to install alsa-driver-linuxant-1.0.23.deb, one place to get it is
[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

- it partly installed, but fails to build new kernel modules
- something about this source is incompatible with kernel 2.6.35-rc1
- at this point i really broke it, no sound on internal speakers or on headphone jack.  GAH! :-(
- tried to reinstall ALSA, pulseaudio, via synaptic, still broken..

- obtained ALSA source snapshot: alsa-driver-1.0.23.75.g04a15.551.ge1b0a
from [http://www.alsa-project.org/snapshot/](http://www.alsa-project.org/snapshot/)

- unbzip, untar, cd to directory, run this configure command line:
- "./configure --with-cards=hda-intel,loopback,hrtimer,aloop"

- run make, then make install
- edit /etc/modprobe.d/alsa-base.conf, add this to end:
options snd-hda-intel model="olpc-xo-1_5"

- reboot, and voila! internal speakers and headphone jack work!  

that procedure got it all working properly for me.  of course, i'm leaving out the rest of the notes from my hours of screwing with compiles and packages, linux kernel variants and ALSA snapshots.. sigh. ;-)

in addition to the linux kernel and ALSA teams and the people on this thread, i also want to mention/thank Morgan Cox (<morgancoxuk@xxxxx) and his thead on archlinux "*Re: alsa-driver 1.0.23 fails to compile with kernel 2.6.35 (archlinux) <msg09290.html>*" from [http://www.spinics.net/linux/fedora/alsa-user/msg09291.html](http://www.spinics.net/linux/fedora/alsa-user/msg09291.html) .  i hope this thread saves other people a bunch of time. ;-)

ttys!

---

### Post by yagolf on 2010-10-10
> **orthopod said:**
> try a fresh install with 10.10 alpha-3 Maverick .  everything works perfectly - battery, cpu scaling, wireless, fans, all cores recognized.
no arguments have to passed to  grub either

i tried updating from 10.04, and that didnt work, but the fresh install did.

I have just done a fresh install with the new stable release of maverick (kernel version 2.6.35.22) and I have to say all problems are still there. I can still get acpi functionality by adding "acpi=copy_dsdt" to the booting options but I haven't solved the microphone/headphones problem. I've tried what spiderman05 suggested but it gets me nowhere :confused:


:guitar:

---

### Post by killernat on 2010-10-12
the "copy_dsdt" fixed the only real problem i had which was the power management then again the "ht" doest  seem to work with 10.10 i just pray it will all be fixed when 11.04 comes out i haven't checked the ethernet yet (my sound works fine) but it sounds like it will work since power management is

---

### Post by spiderman05 on 2010-10-13
I have upgraded to Maverick today. It solved the ACPI problem as mentioned above, provided that you remember to replace "acpi=ht" by "acpi=copy_dsdt". 

Though, I found that the new distribution was very sluggish. I seem [not be the only one]("http://ubuntuforums.org/showthread.php?p=9950880")

I decided to go back to 10.04. This time, I installed kernel 2.6.35-020635rc1-generic. This solved the ACPI problem. I am using option  "acpi=copy_dsdt"

As many already noticed, the Linuxant driver does not work with kernel 2.6.35. The compilation process exits with errors. These errors are generally dumped in some log files under /tmp directory. I followed [these instructions]("https://bbs.archlinux.org/viewtopic.php?pid=822764") to make the compilation go through. I managed to get the driver, though it did not work. (so, don't go that route :))

I then followed the instructions posted by yossman. I compiled the latest build of Alsa ([alsa-driver-1.0.23.83.gd4453.779.ge5ea5.tar.bz2]("http://www.alsa-project.org/snapshot/files/alsa-driver-1.0.23.83.gd4453.779.ge5ea5.tar.bz2")). Everything went well, and I got audio working again). 

B.t.w., Linuxant driver does not allow playing multiple files (say, you cannot play an mp3 on Rythmbox while watching a YouTube video, I had always to close one of the applications and this is one of the main reason I was looking for an upgrade). Installing the latest Alsa driver solved this problem. 

Ethernet is not working. Plugging my ethernet cable brings the Ethernet interface up, but I cannot send or receive any data over it. Wireless works always fine (fortunately). I think that Ethernet works in 10.10, though I am not sure.

I have also installed Kubuntu 10.10 Beta. It works fine (after solving the acpi, pb). I will apply the same procedure to make the sound work. Kubuntu 10.10 is not slow. I might go for it as my default distro as I have been always a KDE user.

---

### Post by killernat on 2010-10-21
ive fallowed your instructions but i cant get it alsa to work right  i have been playing around with diffrent configurations and alsa pakages but im still having problomes and it killed what sound i did have

---

### Post by Seamyst on 2010-10-25
I have a brand-new Toshiba Satellite C655 and am trying to get Lucid running (I don't yet have a Maverick CD). Using the acpi=off option, I was able to actually get into "Try Ubuntu without installing" and then install it from there. (Installed side-by-side with Windows 7, in case something goes screwy.) So far, so good.

Then I go to reboot after the installation is done, and after selecting Ubuntu from the boot menu, I get the exact same screenful of ACPI errors (with the last three lines referring to the kernel). Argh! How do I put in "acpi=copy_dsdt" to prevent these errors, if I can't even boot into Ubuntu?

---

### Post by spiderman05 on 2010-10-26
> **Seamyst said:**
> 
Then I go to reboot after the installation is done, and after selecting Ubuntu from the boot menu, I get the exact same screenful of ACPI errors (with the last three lines referring to the kernel). Argh! How do I put in "acpi=copy_dsdt" to prevent these errors, if I can't even boot into Ubuntu?

Refer to the 1st post in this thread. You will need to add "acpi=off" when you see the GRUB menu. Once you are logged in you need to change grub configuration file to make your changes persistent. Everything is in post #1. I am not sure if "acpi=copy_dsdt" will work for you, use "acpi=ht" instead.

I downgraded from Maverick to Lucid. Maverick is very slow on my computer and it brought more problems than it had solved. I would not recommend it on Toshiba C650D laptops.

---

### Post by Seamyst on 2010-10-26
> **spiderman05 said:**
> Refer to the 1st post in this thread. You will need to add "acpi=off" when you see the GRUB menu. Once you are logged in you need to change grub configuration file to make your changes persistent. Everything is in post #1. I am not sure if "acpi=copy_dsdt" will work for you, use "acpi=ht" instead.

I downgraded from Maverick to Lucid. Maverick is very slow on my computer and it brought more problems than it had solved. I would not recommend it on Toshiba C650D laptops.

Yeah, I went back and found that shortly thereafter. "acpi=off" does indeed work... Unfortunately, I ran into an update problem (unrelated) and can't yet boot back into Ubuntu to do the permanent fix. Sigh.

I've been hearing that Maverick slows down a lot of computers, yeah. I'm definitely sticking with Lucid for now.

---

### Post by killernat on 2010-10-26
> **Seamyst said:**
> Yeah, I went back and found that shortly thereafter. "acpi=off" does indeed work... Unfortunately, I ran into an update problem (unrelated) and can't yet boot back into Ubuntu to do the permanent fix. Sigh.

I've been hearing that Maverick slows down a lot of computers, yeah. I'm definitely sticking with Lucid for now.

aside from the headphone issue i haven't had any trouble from maverick but i would much rather have a working power management than working head phone port

 im going to do another install guide for maverick i just wish i could get the headphone jack working first but every thing i try kills my internal speakers

---

### Post by yagolf on 2010-11-10
Hi everyone!

As of 05/11/10 there is a new BIOS update for the Satellite C650D (model 112) [here]("http://uk.computers.toshiba-europe.com/innovation/jsp/supportMyProduct.do?service=UK") that solves de acpi problem altogether for me (although I've got the feeling they only provide a Windows BIOS flashing application...) \\:D/

> **yossman said:**
> 
- obtained ALSA source snapshot: alsa-driver-1.0.23.75.g04a15.551.ge1b0a
from [http://www.alsa-project.org/snapshot/](http://www.alsa-project.org/snapshot/)

- unbzip, untar, cd to directory, run this configure command line:
- "./configure --with-cards=hda-intel,loopback,hrtimer,aloop"

- run make, then make install
- edit /etc/modprobe.d/alsa-base.conf, add this to end:
options snd-hda-intel model="olpc-xo-1_5"

- reboot, and voila! internal speakers and headphone jack work!  


I tried this and it only screwed the sound even more, now not only do I not have microphone/headphone jacks functioning but I have lost the laptop speakers as well. ](*,)

Is there anybody with this same model that can shed some light on this please?!:cry:

---

### Post by hufemj on 2011-03-03
> **yagolf said:**
> This doesn't work for me. I already have ALSA 1.0.23 and installed the alsa-driver-linuxant_1.0.23.0_all.deb, but there was no change in my system after rebooting, my headphones still don't work... Anybody has more ideas?

Re the problem with the acpi, I have solved it installing kernel 2.6.35 and adding "acpi=copy_dsdt", as recommended [in this bug report]("https://bugs.launchpad.net/ubuntu/+bug/612341")
I have also tried "acpi=ht" and it gives me functionality for both processors as well. As I am quite new to the linux world, I don't know which one's best, but I just thought I'd mention it, I'm sure it'll help someone.

I have another problem that may not belong to this thread but given the fact that we're all concerned with the same machine, I'm going to throw it in and if anybody can point me in the right direction, the more the merrier:
As you all probably know, the Synaptics Touchpad on this laptop supports multitouch and it works fine on Windows but I can't make it work in Lucid. I've tried with gsynaptics and with gpointing-device-settings but none give me the functionality I was expecting.

I really want to have this machine working at its fullest for it is a good computer with a very nice design and running into so many little things is burning me down...:mad:
As I said before, any help would be much appreciated.

:guitar: rock on

Yes!!! Finally! I found some time to work on the ACPI problem with my C655, found this thread, and changing to acpi=copy_dsdt did the trick. Not sure if acpi=ht would work also, but I'm not about to change a thing to find out. This is the first time I've been able to get suspend, shutdown, or hibernate to work with either 10.04 or 10.10.

I should also note that I first upgraded the BIOS to v1.50. It might be that both changes are required to get ACPI to work on a C655.

Thanks!

---

