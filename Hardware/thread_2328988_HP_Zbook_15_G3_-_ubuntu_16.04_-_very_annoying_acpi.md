---
title: "HP Zbook 15 G3 - ubuntu 16.04 - very annoying acpi issue"
date: 2016-06-26
forum: Hardware
---

### Post by blaise2 on 2016-06-26
Hello,
I am the (happy?) new owner of a laptop HP Zbook 15 G3 with i7-6820HQ cpu. 
Since this is not my first laptop and since I never use windows and never had any problem with ubuntu I decided this time not to go for the preinstalled windows. So only freedos was installed.
Trying to boot from the live cd I first had an issue with UEFI and had to go for the legacy mode. 
This was not enough and I had to go for the kernel parameter acpi=off. 
With this I was able to install almost cleanly ubuntu 16.04 (some error messages in the update of some packages but nothing serious)
The huge issue is that with acpi=off ubuntu only sees 1 cpu instead of 8 (and less harmful it doesn't power off when asked to shut down ...)
So I read quite a lot on acpi linux related stuff, found out it is really complicated, and tried the different options for the kernel:
noapic
nolapic
acpi=ht
pci=noacpi
acpi=noirq
pnpacpi=off
pci=nocrs
With none off them I am able to boot. It always ends up with the error message:
NMI watchdog: BUG: soft lockup - CPU #7 stuck for 21s   (numbers vary)

This is very annoying!
Does anybody have an idea of things I could try to fix this if it is possible.
Thanks 
Blaise

---

### Post by blaise2 on 2016-07-04
Hi,
For those interested, it has been possible to install ubuntu 16.04 by removing the UEFI option and the hybrid graphics in the BIOS and keeping acpi. Thanks jml and rr for that.
Now second problem: the thunderbolt 3 dock is not seen at all by the os, only power supply works. It seems hp does not provide the driver for this. Did anyone manage to have this working?

---

### Post by thanh-binh on 2016-07-05
Hi,
I installed Ubuntu 14.04 LTS, but it crashed by Shutdown.
The upgrade to Ubuntu 16.04 LTS failes somehows.
I need your solution too.
could you please give me your installation guide step by step?Thanks.

---

### Post by blaise2 on 2016-07-05
Hi,
As I explained in my previous post I did only 2 things eventually in the BIOS
1- change the UEFI boot option to legacy boot option
2- change the Hybrid Graphics option to Discrete Graphics option
With these 2 changes I was able to install ubuntu 16.04 properly from a live CD.

The thunderbolt 3 issue remains unsolved for the moment ...
Good luck

---

### Post by X-RED_Tech on 2016-07-05
> **blaise2 said:**
> 1- change the UEFI boot option to legacy boot option
Not needed and may well be the root cause for some hardware not being recognized.

> 2- change the Hybrid Graphics option to Discrete Graphics option
OK.
Then you should install the recommended proprietary Nvidia drivers so you can switch cards (reboot needed).

> With these 2 changes I was able to install ubuntu 16.04 properly from a live CD.
It's a DVD and you shouldn't be using disks. Use a properly done USB flash drive (Rufus in Windows and MKUSB in Ubuntu highly recommended; in Rufus make sure you check UEFI/GTP support).

> The thunderbolt 3 issue remains unsolved for the moment ...
Probably because you're booting in legacy mode and/or have it disabled in UEFI.

---

### Post by thanh-binh on 2016-07-12
> **blaise2 said:**
> 
2- change the Hybrid Graphics option to Discrete Graphics option


I do not find any option in BIOS for changing it.
Some HP documents say that only Discrete Graphics is available for workstation.

Is it any mistake here?

thanks for help, Binh

---

### Post by zothen on 2016-07-18
> **blaise2 said:**
> Hi,
As I explained in my previous post I did only 2 things eventually in the BIOS
1- change the UEFI boot option to legacy boot option
2- change the Hybrid Graphics option to Discrete Graphics option
With these 2 changes I was able to install ubuntu 16.04 properly from a live CD.

The thunderbolt 3 issue remains unsolved for the moment ...
Good luck

Hello, me and my co-worker had this problem as well but on the Zbook Studio. We resolved it by going into BIOS -> Advanced -> Ports -> (I can't remember the rest) and find and disable a security setting there. After that, the Thunderbolt 3 hub was recognized and worked fine.

---

### Post by blaise2 on 2016-07-18
Sorry thanh-binh I told you all I know ...

---

### Post by blaise2 on 2016-07-18
Hello zothen,
Thanks for your post. I think I already tried this but nevertheless I will check again

---

### Post by estownya on 2016-09-20
> **blaise2 said:**
> Hello zothen,
Thanks for your post. I think I already tried this but nevertheless I will check again

Hello blaise2,

any update on the issue? I am asking because I am thinking of purchasing a Zbook 15 G3

---

### Post by prabha222 on 2016-09-21
I'm having trouble booting Ubuntu 16.04 on HP Zbook 15 G3, installation goes through but bootup lands in "initramfs" prompt.
I have tried both legacy and UEFI mode.

Can anyone confirm if grub needs to be installed on the nvme root partition or the drive? Partition config will be useful too.

---

### Post by embepi on 2016-10-12
I've got the same problem with initramfs, any solutions?

---

### Post by simondcoleman on 2016-10-14
I have a zbook g3 from a couple of weeks ago & is working very well with current xenial release, with a single exception - unable to resume from suspend (so repeatedly having to restart from a crashed state).
V. annoying, since everything else (multiple displays, docking station, handling for multiple networks via wifi/wired/docked) is all very good & the underlying O/S very robust [I have also updated to gnome 3.20]
I may have to go back to windows if I cannot solve the power issue very soon though.

---

### Post by Brian_Axelrod on 2016-10-29
> **simondcoleman said:**
> I have a zbook g3 from a couple of weeks ago & is working very well with current xenial release, with a single exception - unable to resume from suspend (so repeatedly having to restart from a crashed state).
V. annoying, since everything else (multiple displays, docking station, handling for multiple networks via wifi/wired/docked) is all very good & the underlying O/S very robust [I have also updated to gnome 3.20]
I may have to go back to windows if I cannot solve the power issue very soon though.

HP also lists official ubuntu compatibility here [http://h10032.www1.hp.com/ctg/Manual/c00060684.pdf](http://h10032.www1.hp.com/ctg/Manual/c00060684.pdf)

---

### Post by Napseis on 2016-11-02
hi,
I have a Zbook 15 G3 as well from the work.
Right now i have opensuse:
If i keep hybrid graphics, the backlight is always at maximum. So i have enable discrete only. I disable secure boot, the system is on the nvme ssd drive.

For me, for any distro (Ubuntu, Opensuse); I must disable in the bios "runtime power management", otherwise i get different kind of crashes, kernel panic, etc... But this disable turbo boost :(
Unless i set acpi=off: then , it boots, but i see only one core, and turbo boost is working in this case 

This drives me mad.

---

### Post by jacob-nordfalk on 2016-11-10
Hello,

I also had problems booting. It seems it was solved adding pnpacpi=off in the boot command line (edit /etc/default/grub and doing 'sudo update-grub' afterwards).

I also enabled legacy mode, but I i'm not sure that made any difference.

Jacob

---

### Post by Napseis on 2016-11-10
hi,
I just tried, in UEFI mode, no luck. Same panics.
I cannot afford to switch to legacy right now, i'll try this week end, but i would be surprised if it worked.

edit: legacy didn't help. I think this should be RMA, according to all the post we see on Skylake.

---

### Post by jacob-nordfalk on 2016-11-16
Hi there,
I have testet a lot and and can confirm that Ubuntu 16.10 works out of the box.

In Ubuntu 16.04 it works for me if I
1) Change so I use NVIDIA binary (I use version 367.57) instead of Nouveau driver (which gives a GPU lockup or something)

2) Set pnpacpi=off  in the boot (and remove the quiet splash etc stuff)
This can be done from GRUB pressing 'e' and replace "ro quiet splash" etc with just "ro pnpacpi=off" and booting pressing F10
To do it permanently edit /etc/default/grub to have
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="pnpacpi=off"
and do 'sudo update-grub'

To get into the system and make the changes I had to boot into rescue ("rescue" as parameter in GRUB).

BTW - in the process of experimenting I also had to temporarily disable graphical startup. I did this with
sudo systemctl set-default multi-user.target
and then I only had a prompt where I could do this to start graphics manually:
sudo /etc/init.d/lightdm start

To revert to graphical startup do:
sudo systemctl set-default graphical.target


This is all with these BIOS settings:
[COLOR=#000000]1- change the UEFI boot option to legacy boot option[/COLOR]
[COLOR=#000000]2- change the Hybrid Graphics option to Discrete Graphics option[/COLOR]

---

### Post by zothen on 2016-11-19
I just received my 2nd Zbook Studio G3 (first one died, took 3 or 4 months for the re-order to arrive).

I have various issues but the main issue I'm having is that I can't connect to an external monitor over hdmi over using Display Port via the HP Thunderbolt 3 docking station. The docking station firmware was updated (using Windows) to the latest firmware they have on their website.

One difference I have compared to Jacob's experience is that I have to use the "Hybrid" graphics option in BIOS or else gdm never starts using Discrete mode (Using Ubuntu Gnome 16.04).  Using "Intel" using "prime-select intel" or nvidia using "prime-select nvidia".  I'm using nvidia-367 drivers, kernel 4.8.0.27.  I am also setting "pnpacpi=off" in the grub / kernel command line and using legacy UEFI mode.

Both external monitor options (HDMI or Displayport via Thunderbolt 3 docking station) work fine in Windows.  In Ubuntu, using the "Displays" application it shows no external monitors.

Any suggestions?

---

### Post by jacob-nordfalk on 2016-11-22
My HDMI port also doesent work, so I just use VGA. 
I didnt try with a docking station.

My suggestion would be to try with Ubuntu 16.10 (for example make a small partition and install it there from scratch and then upgrade all packages), as evrything ive tried seems to work there.

---

### Post by columgaynor on 2016-11-25
@jacob-nordfalk
Thanks for your tips in this case. I now finally succeeded to make a USB stick installation of Ubuntu 16.10.
I selected the option download third party SW which had the effect to TURN OFF THE SECURE BOOT.
I found things to work, even without changing to the NVidia driver, which you advertised.
(I ran into issues when I tried that driver actually).

However I am left with one major failure - the Wireless LAN is not working at all.
As far as I understood you have not had issues with the Wireless LAN - is it so ?
I posted the dmesg outputs at [http://paste.ubuntu.com/23531731/](http://paste.ubuntu.com/23531731/) and made a
short analsyis of all messages flagged up in red font colour in mt Ubuntu terminal.
The analysis is at [http://paste.ubuntu.com/23532267/](http://paste.ubuntu.com/23532267/).

I probably need to post this problem and help request to specific forum dealing with WiFi,
but if you have any ideas what is behind this HP ZBook 15 G3 final issue; I'd appreciate your help/opinion.

Best regards Colum Gaynor

---

### Post by columgaynor on 2016-11-25
@jacob-nordfalk
Ignore last request .... Just found the solution at: [https://ubuntuforums.org/showthread.php?t=2340876&highlight=Intel+8260+ac](https://ubuntuforums.org/showthread.php?t=2340876&highlight=Intel+8260+ac)

---

