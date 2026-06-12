---
title: "Fujitsu Amilo A 7620 laptop freezes during installation proccess."
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by qra on 2009-09-14
Installing Ubuntu 9.04 to a Fujitsu Amilo A 7620 laptop, freezes during writing to disk at about 20-30% of the installation proccess.
I tested all the possible commands found in forums at boot installation without success.
Same thing happens with suse linux 11.1.
Finally I installed suse 11.1 through network installation without any problem,(Is there something like this for Ubuntu?)
When I try to check the suse installation dvd media through the properly installed program, the whole system freezes and needs restart (power off and power on).
The freezing happens when request a heavy operation from the dvd (NEC ND5100A) and not when I do a dir to the dvd.
Any idea please?:confused:

---

### Post by scorp123 on 2009-09-14
> **qra said:**
>  Any idea please?:confused: 

You are not alone and not the first one to report this:
[http://ubuntuforums.org/showthread.php?t=1059075](http://ubuntuforums.org/showthread.php?t=1059075)


That laptop that you have is an Ex- Fujitsu-Siemens. Fujitsu-Siemens was dissolved recently when Siemens quit the joint-venture with Fujitsu ... But unfortunately their stupid broken laptops live on.

Which leads us to what I am trying to tell you: Fujitsu-Siemens laptops suck badly. I have owned a few during my career and I was very happy to get rid of them as soon as I could. **If you can: return your laptop.** Make something up if you have to. Unfortunately most shops won't accept "doesn't run well with Linux" as a valid explanation. Simply say "it freezes all the time" and insist on having your money returned ... if you can.

The main problem with all Fujitsu-Siemens laptops is that quite many of them seem to have some braindead not-exactly-sticking-to-standards BIOS and/or interrupt controller ... And as soon as you try to do something ACPI-related it will freeze.

One of the laptops I owned was a Fujitsu-Siemens Lifebook C1410 and to get that one to work I had to add this option to the boot parameters of the Linux kernel: ```
pci=usepirqmask

```

Apparently this changes the way by which the kernel will try to talk to internal devices ... and it helped in my case.

Maybe you want to try that?

Here is how:

- Open a terminal
- temporarily become "root" and edit the "menu.lst" file:
```
gksudo gedit /boot/grub/menu.lst
```
- the boot loader's config should have loaded
- find the line saying:
```
...
# defoptions=quiet splash
...

``` (search for the word "defoptions" ...)

- now add the stuff I mentioned above so that the line now looks like this:
```
# defoptions=quiet splash pci=usepirqmask
```
- save and close

Once the editor has closed, please issue this command:
```
sudo update-grub
```

Reboot .... and find out if it worked. If your system still freezes: Sorry ... in that case it didn't work.

Googling around I found some German guy's PDF (in English):
[http://familieriedel.fa.funpic.de/a7600/amilo_linux_eng.pdf](http://familieriedel.fa.funpic.de/a7600/amilo_linux_eng.pdf)

He seems to have an Amilo 7600 which should be similar enough to your model. Maybe the stuff in that PDF is of some use?

---

### Post by qra on 2009-09-14
Hi scor123 and thank you for yr fast and full of info answer.
Anyway it looks like a whole university to study and apply all of them.
It has taken two weeks of time trying to install a linux distribution to the current laptop. I have downloaded and re-downloaded tenths of gbs and burn a lot of cds and dvds.
I have or had a feeling that a new dvd firmware could solve the problem.
i will try and keep you informed.
Thnks agn

---

### Post by orawax on 2009-11-03
> **qra said:**
> Installing Ubuntu 9.04 to a Fujitsu Amilo A 7620 laptop, freezes during writing to disk at about 20-30% of the installation proccess.

I installed *Ubuntu 9.10 Karmic* successfully on an Amilo A 7620 by using the [_Minimal installation CD_](https://help.ubuntu.com/community/Installation/MinimalCD) ([_.iso_](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/mini.iso)).

Booting from the cd, I added these options:
```
pci=usepirqmask hdc=noprobe hdc=cdrom
```
and perhaps I also disabled acpi, can't remember...

In 9.04 the installed system became unresponsive when you put a disc in the dvd/cd-drive, but in 9.10 the dvd-drive seems to work out of the box. There's still one problem I'm experiencing: the mouse/cursor behaves erratically or hangs for a while repeatedly.

By the way, I think I'll be always using the minimal cd from now on: it allows installing an encrypted filesystem, and "the download time savings achieved by using a Minimal CD can be significant, as only current packages are downloaded, so there is no need to upgrade packages immediately after installation."

---

### Post by Kanarmada on 2011-07-18
thanks a lot [orawax]("http://ubuntuforums.org/member.php?u=46108").
I also tried to install Linux on this machine during the last 14 days and used nearly every distribution I could find (from ubuntu 7.04 over Suse, debian, Solaris and so on). It always freezed somewhere in the process. But with the minimal iso (which I havn't known before) it was no problem.
I also think about about using it for every installation, it's very usefull, also the possibility to encrypt the whole system, not only the home folder.

Funny how many work somebody is willing to do, if he don't want that his child uses windows. ;-) 

bw

---

