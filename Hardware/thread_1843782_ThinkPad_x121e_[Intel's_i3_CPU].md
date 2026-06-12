---
title: "ThinkPad x121e [Intel's i3 CPU]"
date: 2011-09-14
forum: Hardware
---

### Post by krzyh00 on 2011-09-14
Hi there,

just unpacked my sexy x121e with Intel's i3. Here's my short review which should help you avoid some pitfalls, that made me almost cry yesterday.

Forst and foremost - without tweaking BIOS you will fail to boot it from a stick. UEFI needs to be disables. Symptoms: a stick created wit unetbootin booted fine on my desktop; immediately a nice unetbootin log-in screen was visible. Same stick on my shiny x121e booted with GRUB instead of unetbootin (1st of way to many many 'WTFs' that day) and regardles of the option I choose, the entire machine hanged after a while (usb's led stopped blinkng as well)

Second - even if the installation on 11.04 is successfull, there is a chance you will not be able to boot from the hard drive. Symptoms: Error message stating that there is "No operating system". This was however discussed in other posts.

Third - x121e has no hard on/off Wi-fi switch. So if you have problems enabling wireless nic and it has been properly detected and installed (ifconfig displays wlan0, buit there is a remark that the card is off) try the following:

  - "rfkill list" (this will display all adapters which are radio frequency enabled; find the number next to your wlan and:
  - "rfkill unblock <NUMER>"

This did the trick for me

Fourth - if you discover that your wireless lan connection is extremly slow (I mean modem slow, even though you have perfect signal, and wireless manager says you're cruising at 13 Mbits, try and disable the n-mode in your wireless router. Did the trick for me :)

Enjoy

---

### Post by - Lo - on 2011-09-20
Hey krzyh00,

I am looking for the x121e too.

What do you think about it?
Does it works well?
What about the battery life?
What about the overall performances?
What about working on it 8-hours a day? 

Thanks in advance :)

Lo

---

### Post by jheyman on 2011-09-20
Hello,
I bought the same laptop with windows 7 preinstall on it. I wanted to install ubuntu but no way to boot from the usb stick.

I tried as you say to put Legacy instead of UEFI in the bios config, but without success.

I tried Diagnostic mode also. Nothing. I tried to boot manually with F12 key, it recognizes mw usb stick, bt when I press enter, it load a bit and then goes back to the boot screen, or load windows instead...

I tried to use unetbootin instead of the universal ub boot creator but without success (although it works on other laptop)


I tried 10.04.3 LTS in 32 bit and 11.04 in 32 also but without success...

I'm beginning to be a bit worried of the capability of this laptop to support linux... And I'm allergic to windows.... :(

Considering the partionning problem, do you think it happens also with the 10.04.3 version ?

Thanks for help,
Joris

---

### Post by srs5694 on 2011-09-20
I can make no promises, but you might try this to get a unetbootin-created USB flash drive to boot and install Ubuntu:


[list=1]
[*]Prepare the unetbootin disk in the usual way. Be sure to use an AMD64/x86-64 version of Ubuntu; this procedure probably won't work with an i386/x86 version.
[*]Extract elilo-3.14-x86_64.efi from [ELILO](http://elilo.sourceforge.net/cgi-bin/blosxom) (download a tarball [here](http://sourceforge.net/projects/elilo/files/elilo/elilo-3.14/elilo-3.14-all.tar.gz/download)). Copy elilo-3.14-x86_64.efi to the /efi/boot directory on the unetbootin disk. It may help to rename this file so that it replaces the bootx64.efi file that's already there. For instance, if your unetbootin disk is mounted at /media/efi, you would type, from the directory to which you've extracted ELILO, "cp elilo-3.14-x86_64.efi /media/usb/efi/boot/bootx64.efi". You could do this in Windows, if it's more convenient.
[*]Create a file called elilo.conf in the unetbootin disk's /efi/boot directory (the same directory that now holds the elilo-3.14-x86_64.efi file). It should have the contents shown below.
[*]Reboot the computer.
[*]Using the firmware utility, turn *on* EFI boot mode.
[/list]


The elilo.conf file should look like this:

```
prompt
timeout=50
default=tryitnow

image=../../install/vmlinuz
        label=install
        initrd=../../install/initrd.gz
        read-only
        append="file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --"

image=../../casper/vmlinuz
        label=tryitnow
        initrd=../../casper/initrd.lz
        append="file=/preseed/ubuntu.seed boot=casper quiet splash --"

```

I'm unfamiliar with the firmware in the ThinkPad x121e under discussion here, so I'm afraid I can't offer specific steps from this point. If you're lucky, you'll see an option to boot from the USB drive when you enter whatever boot options menu you've got. If not, you may need to create a new entry in the firmware. It might also be necessary to copy the contents of the USB drive's efi/boot directory to the EFI System Partition (ESP) on the computer's hard disk. If you do so, you may need to rename an existing directory of that name or rename the one you're copying.

If these steps are successful, you'll end up booting the Ubuntu installer in UEFI mode rather than in BIOS mode. This procedure replaces the installer's normal use of GRUB 2 to boot on UEFI systems with ELILO, which in my experience is more reliable. (You may need to do a similar replacement, and add [rEFIt](http://refit.sourceforge.net), to the finished installation to get it working 100% reliably. That's another topic, so post back if and when you get to that point.) ELILO gives a simple "ELILO boot:" prompt, and the configuration file above gives you two options -- "install", which boots the installer, and "tryitnow", which boots the system in its "try it now" mode. On my test system, the "install" option ran in text mode, but "tryitnow" booted to a full GUI, so you might prefer it. In any event, the configuration I've provided boots to the "try it now" mode after a timeout of 5 seconds; or you can type either option to boot it explicitly.

A UEFI installation has some advantages over BIOS mode, but unfortunately, the Ubuntu installer's UEFI support is still weak -- at least, as of 11.04; things may have improved with the latest 11.10 beta). Some things you should beware:


[list]
[*]The Ubuntu installer tends to wipe out the EFI System Partition (ESP) -- normally the first partition on the hard disk. The ESP holds boot loaders, including one that's vital for Windows to boot. Thus, after installing Ubuntu, Windows may not boot. If you do so, you can restore the backed-up files after you do the installation to make Windows bootable again. You can back up the ESP in the "tryitnow" mode by mounting the ESP (normally /dev/sda1) and doing a simple file copy. (Unlike MBR boot loaders, UEFI boot loaders are normal files on a filesystem, so they require no special programs to back up or install.)
[*]If you use the manual partitioning option, you've got to explicitly tell the installer about the ESP. IIRC, Ubuntu's installer calls it an "EFI boot partition," so you've got to select the ESP and flag it as such. You do not explicitly give it a mount point, but after a successful installation, it will be mounted at /boot/efi.
[*]The installer will install GRUB 2 to the ESP, so after installation, you should be able to boot using GRUB 2. Unfortunately, this sometimes works and sometimes doesn't work. (On one of my systems, GRUB 2 boots the computer only about 1 in 4 tries, so give it a few tries if it doesn't work the first time.) If it doesn't work reliably, you can install ELILO to your hard disk's ESP. You'll need to copy your Linux kernel and initial RAM disk there, too, and modify the elilo.conf file to point to your regular kernel and initial RAM disk.
[/list]


This should all become much easier as Ubuntu improves its UEFI support. From a systems engineering perspective, this isn't really that hard -- all of the pieces exist, and it's just a matter of putting all the files in the right places and putting the right entries in the configuration files. The problem is that the Ubuntu installer doesn't yet do it quite right, so if you don't understand the topic (few do as of yet), it's like trying to find your keys in an unlit field at night.

---

### Post by krzyh00 on 2011-09-21
> **- Lo - said:**
> Hey krzyh00,

I am looking for the x121e too.

What do you think about it?
Does it works well?
What about the battery life?
What about the overall performances?
What about working on it 8-hours a day? 

Thanks in advance :)

Lo

So far I've had some pretty decent experience with this one. I like the finish, keyboard is really great (feels like your fingers are dancing on it), it is really quiet compared to my old Toshiba L20-101. And most certainly it feels really robust. You know those squeaks of dying plastic every time you pick up a laptop? Not here my friend.

With regards to the battery life, the promised 7 hours is science fiction. If you use it the way I do (wireless always on, full brightness, power savings off) than you'll easily make 4,5 hrs. So far I was not in need to do some power saving tweaks. But 4,5 hrs is a good starting point.

Performance is really nice. I was able to play hd videos, the computer boots up really quick. All in all I haven't noticed any extreme lags or performance issues. My expectations were met in full.

Working 8 hours a day? depends on kind of work you do. Personally, I have an 24" desktop at home as SIZE DOES MATTER. I bought this laptop for couch-surfing while my wife is enjoying another one of them "oh-god-i-love-him-but-we-cannot-be-together-cause-he-is-marrying-that-other-girl" chick flicks :-) But it is an excellent piece of hardware if you require mobility. If you fly or travel by train, you know how small those trays are, don't you? My old laptop didn't fit in there. This one does and I love it.

What I dislike? Well the LCD Matrix is not a top notch. If you look at it from a sharp angle, you get this feeling of either colors getting inverted (looking up at the screen) or the screen gets dark (looking from left or right at the screen). But considering, that this laptop is not sold as multimedia tank, I knew about it beforehand and I accept it.

Hope it helps.

---

### Post by krzyh00 on 2011-09-21
> **srs5694 said:**
> 
A UEFI installation has some advantages over BIOS mode, but unfortunately, the Ubuntu installer's UEFI support is still weak -- at least, as of 11.04; things may have improved with the latest 11.10 beta).


Quick question: What are those advantages? I'm talking about installing on a laptop with NO PRE-INSTALLED SYSTEM WHATSOEVER.

---

### Post by srs5694 on 2011-09-21
> **krzyh00 said:**
> [quote=srs5694]A UEFI installation has some advantages over BIOS mode, but  unfortunately, the Ubuntu installer's UEFI support is still weak -- at  least, as of 11.04; things may have improved with the latest 11.10  beta).Quick question: What are those advantages? I'm talking about installing on a laptop with NO PRE-INSTALLED SYSTEM WHATSOEVER.[/QUOTE]

Some of these are very minor and/or apply only to certain configurations; but what comes to mind is this:


[list]
[*]UEFI boots are usually a bit quicker than BIOS boots (by about 20 seconds, in my experience -- although that's based on an EFI-based Mac, and so might not be applicable to UEFI-based PCs).
[*]With Windows installed, UEFI enables use of GPT for the boot hard disk. GPT has its own set of advantages, the most important being support for over-2 TiB disks. GPT also lacks the primary/extended/logical partition distinction and is theoretically more robust against damage. If you don't want to install Windows, none of this applies, since Linux supports booting from GPT disks even on BIOS-based computers.
[*]UEFI's boot process uses boot loaders that are stored as ordinary files on a filesystem. In theory, this makes boot loader maintenance easier and makes co-existence of multiple boot loaders easier. In practice, the UEFI support in GRUB 2 and Ubuntu is poor enough to overpower this advantage at the moment, but once GRUB 2 and Ubuntu get it together, it'll swing the other way.
[*]UEFI provides a shell, the ability to run shell scripts, the ability to load drivers, and other features normally associated with an OS. At the moment, those features aren't used for much; but in time they could be. You might be able to write a shell script to heavily customize your boot process -- say, to detect which network your computer is on and to boot a different OS for each network.
[/list]

---

### Post by jheyman on 2011-09-22
Thanks for your long answer SRS! I may try the UEFI option. But what I don't understand is why I can't boot my usb key, even under the Legacy mode, although it is booting on other computers?...

Also, when I try UEFI only, windows doesn't boot, meaning that windows need a normal bios ?

I checked the firmware a bit more closely, there is a parameter for the usb port : UEFI support enable. I tried to disable it but then, the key is not working at the beginning (no red light). It also precised that Disabling this option will makes you unable to bnoot the key.


How did you do krzyh00 ? How did you create the usb key and how did you manage to "tweak" the firmware ??

Thanks a lot,
joris

---

### Post by srs5694 on 2011-09-22
> **jheyman said:**
> Thanks for your long answer SRS! I may try the UEFI option. But what I don't understand is why I can't boot my usb key, even under the Legacy mode, although it is booting on other computers?...

I'm afraid I have no answer to that question. Perhaps I could figure it out with some hands-on time with your specific computer, but that's obviously impossible online.

> Also, when I try UEFI only, windows doesn't boot, meaning that windows need a normal bios ?

Windows needs to boot in whatever mode was used to install it. This *can* be changed, but it's a bit tricky. If you want details, check [this article](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI) for information on how to switch Windows from BIOS to UEFI booting.

---

### Post by jheyman on 2011-09-22
ok thks for your answer.
All I needed is empathy :)

I will continue to fight alone. If somebody get an advice, please let me know.

My next step will be to boot on a external usb disk reader to boot from an ubuntu cd.


Hopefully in some week I'll post good news ;)
Cheers !
jo

---

### Post by jheyman on 2011-09-23
Hey there,

I tried the trick you told me with the elilo.conf file and the bootx64.efi in the /efi/boot directory!.

I succeed finally to boot on the usb key in UEFI only mode:

It was written :
Elilo boot:
Then it loads 2 files, and writes "done" for each of them. Then it stops loading and the usb key turn off. The screen stays the same....

What 's the matter ?

Thank you !
Joris

---

### Post by kurt18947 on 2011-09-23
I'm not sure my solution will work for you but I had a problem with USB drives booting on one machine, it booted fine on others.  I formatted it in Windows 7 (took *forever*) but they now boot on this machine.  The problem machine has a Gigabyte M.B. with an Award modular BIOS, no UEFI support.  But formatting in Windows 7 then creating the LiveUSB with Unetbootin did cure my boot problem.  Prior to the Windows 7 format I'd either get a "boot error" or maybe "grub rescue" message.  I hope this is of some use.

---

### Post by srs5694 on 2011-09-23
> **jheyman said:**
> Hey there,

I tried the trick you told me with the elilo.conf file and the bootx64.efi in the /efi/boot directory!.

I succeed finally to boot on the usb key in UEFI only mode:

It was written :
Elilo boot:
Then it loads 2 files, and writes "done" for each of them. Then it stops loading and the usb key turn off. The screen stays the same....

What 's the matter ?

Several possibilities spring to mind:


[list]
[*]There could be an error in the elilo.conf file -- a typo, an incomplete cut/paste, etc. Note this includes both errors copying it on your end and errors on my end; and it could be that what works fine for me fails on your computer and so could be considered an "error." Double-checking the file with what I posted, and perhaps studying the format and trying variants, might be worth trying. You could try removing the "quiet splash" options to get the kernel to display boot-time messages for more diagnostic information, for instance.
[*]You could try the other boot option by typing "install" at the "ELILO boot:" prompt. That should launch the installer directly, rather than launch the desktop environment. On my test system, the installer ran in text mode when launched this way, but at least it did run.
[*]The kernel provided by Ubuntu might be incompatible with your computer's hardware. Perhaps an upgraded kernel (most easily done with a more recent version of Ubuntu) would do better, or you might have better luck with another distribution (Fedora, OpenSUSE, Debian, etc.).
[*]It could be that the system has booted but that there's a problem with the video interface. I've seen this on some UEFI boots, but mostly on VirtualBox installations. This could be tricky or impossible to get around, since without the display, you have no interface to the computer. (On my VirtualBox installs with this problem, I've been able to boot in other ways, enable an SSH server, reboot in the problem way, and log in via SSH to verify that the system has booted but doesn't have a display.)
[/list]


One other thought occurred to me, regarding a BIOS-mode boot: Some of my systems have problems booting from some of my USB flash drives in BIOS mode. The problem appears to be tied to specific USB flash drives; for instance, a 2 GB PNY drive is unbootable on some of my computers, although it works fine as a non-boot data drive and is even bootable on other computers. You could be seeing something similar, in which case using a different USB flash drive might be a way to work around the problem.

---

### Post by jheyman on 2011-09-24
Thks srs, I read carefullfy your explanations. I go to buy a new usb key. Maybe it will be my salvation...

---

### Post by jheyman on 2011-09-24
IT WORKED ! I bought  new SanDisk 8gb USB key and it boots without problem ! 

The BioDrive Disk2go.com I was using seems to be the cause of my troubles.

Thanks a lot for everybody help,
Joris

---

### Post by MorrisseyJ on 2011-10-03
Hi,

I am not sure if this will help future readers with boot problems on the x121e.

[https://answers.launchpad.net/ubuntu/+question/168297/+index](https://answers.launchpad.net/ubuntu/+question/168297/+index)

---

### Post by JENSON10 on 2011-11-14
I have a x121e as well. I am using ubuntu 10.10 but cannot detect any wireless connections. The Broadcom a/b/g/n chipset has no drivers available, wish I had bought it with an Intel WLAN chip :(

---

### Post by Dead1nside on 2011-12-03
Just wondering what sort of temperatures other users are getting with i3 X121e's? I'm getting 55-65 degrees celsius at idle, and up to 75 degrees at load. Has anyone managed to improve on this? Perhaps the fan isn't running at full-speed by default on mine. Thinkpad-acpi reports it is in 'auto' mode at 600RPM.

Thanks.

---

### Post by zibletop on 2012-01-16
Hi,

The thread linked below could be useful to install and configure the x121e

[[ubuntu] Lenovo x121e i3 Linux Hardware Compatability - Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=1894892)

---

### Post by MorrisseyJ on 2012-01-30
Hi Dead1nside,

I had similar problems. Following the instructions here:
[http://www.omgubuntu.co.uk/2011/11/linux-power-regression-overheating-problem-on-thinkpad-fixed/](http://www.omgubuntu.co.uk/2011/11/linux-power-regression-overheating-problem-on-thinkpad-fixed/)

i knocked about 10 degrees off the temperature. 

Also installing the Jupiter applet ([http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)) let me configure the power settings. Now temperatures only get high if its on max power setting or 'on demand' and i am doing some demanding work. Otherwise its about 48 deg.

Hope this helps.

---

