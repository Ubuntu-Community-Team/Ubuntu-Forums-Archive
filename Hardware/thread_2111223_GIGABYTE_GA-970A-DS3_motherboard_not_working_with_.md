---
title: "GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel"
date: 2013-02-01
forum: Hardware
---

### Post by 6tonspacefly on 2013-02-01
I recently upgraded my computer and purchased a GIGABYTE GA-970A-DS3 motherboard. If I boot off of a live CD with any 32bit distro - it has to be a live CD since it doesn't boot of a USB - then everything works. If I boot off of a 64bit distro live CD, it'll load, but the USB ports don't work, neither does the on-board Ethernet as well as a PCI wifi card I installed as an attempted work around.

I also attempted to install a 64bit distro, Ubuntu 12.10, and then manually install a newer kernel. This did not fix the problem, no matter the kernel version.

I've looked around online for a solution, but I can't seem to find any posts where people are having the same troubles as I am.

Thank you.

Current specs:
GIGABYTE GA-970A-DS3
AMD Phenom II X4 965 Black Edition AM3

---

### Post by Grinage on 2013-02-01
GIGABYTE 3x USB Power with On/Off Charge USB ports
USB 3.0 with superspeed transfer rates of up to 5 Gbps


It could be a BIOS setting regarding USB Legacy support, the ethernet is a different story though, can you clarify for me what the system thinks the nic is when it's working and when it's not working, use 

lspci | grep net

or 

lshw | grep net

---

### Post by Mark Phelps on 2013-02-01
Did you check the Gigabyte forums to see if they could help?

Asking because I have a Gigabyte GA-890GPA-UD3H and could not get the wired onboard nic to work reliably until, in Windows, Gigabyte came out with new RealTek drivers and a diagnostic utility. 

The NIC would turn on in Windows but when I rebooted into Ubuntu, it would indicate no network.

When I went back into Windows, I would have to run the diag routine to MANUALLY turn the NIC back on.  Then it would work.

But, when I booted back into Ubuntu, same problem again.

It took three driver updates to get it working right.

Maybe on the Gigabyte forums, someone has figured out how to fix this in Linux for your board.

---

### Post by Luke3026 on 2013-02-01
I just got the same board as the original poster (Rev. 3.0) and can confirm the same problems -- onboard ethernet not working and only the 2 USB3 ports working (all other USB ports dead).

I was trying to install Xubuntu 12.04, then 12.10 (all 64-bit) with nothing but frustration until I saw this post.  Tried a 32-bit version of Mint, and all is working.  

I know someone with an older Rev. of this board and it does work with 64-bit distros, but evidently Rev. 3.0 is a no-go.  I imagine Gigabyte will fix this in some update.  Until then, I'll just stick with the 32-bit install.  After 3 days of frustration with this thing, I'm just happy to get something working.

---

### Post by Grinage on 2013-02-01
I noticed that there are bios updates for this product, have you tried updating the bios and if yes was the result the same?

Sorry if I ask a question that may seem unrelated, in my dayjob I'm a hardware tech and odd interactions between software and hardware are things I'm keenly interested in finding solutions for before I have to face an angry customer.

---

### Post by Luke3026 on 2013-02-02
I updated the BIOS to the latest firmware, and both problems still exist with the 64-bit kernel.

---

### Post by Grinage on 2013-02-02
Thanks, that helps eliminate the obvious.  Next question, when you attempt to install the 64-bit distro or the 32-bit, does it find the nic and connect to the internet during installation, there is a screen that asks about connecting to the internet to download updates during installation.

I'd still like to see what the machine thinks it has or doesn't have for a nic.  The OP stated that when he ran off the 32-bit live cd everything worked, but when he tried to actually install it then things began failing.    If the networking situation could be resolved, a backports repository might resolve the USB situation

---

### Post by Yellow Pasque on 2013-02-02
Why won't it boot USB? Note that Ubuntu 12.10 doesn't fit on a standard CD, so that may be an issue..

---

### Post by Grinage on 2013-02-02
Interesting note on this motherboard.  The chipset for northbridge is not supported under a linux 64 bit kernel and neither is the Southbridge according to AMD's own website.

[LIST=1]
[*]North Bridge: AMD 970
[*]South Bridge: AMD SB950
[/LIST]


When you go searching around for information from Gigabyte and AMD there's a distinct lack of it concerning linux 64 bit kernels.  This may have been one of those 'made for windows' boards so it may take some time before manufacturers decide to get around to the rest of us.


There may be some patches for the next in the line of kernels if you want to attempt it from


[http://www.kernel.org/](http://www.kernel.org/)




I wish I had better news or more information to give.

---

### Post by Yellow Pasque on 2013-02-02
I find that hard to believe. Please cite the AMD page that says that. The 970/SB950 is just a small update to the 870/SB850, and I know that chipset works well with Linux.

It may be this bug, which requires an updated BIOS from the manufacturer, unfortunately: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/859137](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/859137)
Try disabling the IOMMU.

---

### Post by Luke3026 on 2013-02-02
> **Grinage said:**
> Thanks, that helps eliminate the obvious.  Next question, when you attempt to install the 64-bit distro or the 32-bit, does it find the nic and connect to the internet during installation, there is a screen that asks about connecting to the internet to download updates during installation.

I'd still like to see what the machine thinks it has or doesn't have for a nic.  The OP stated that when he ran off the 32-bit live cd everything worked, but when he tried to actually install it then things began failing.    If the networking situation could be resolved, a backports repository might resolve the USB situation

On a 64-bit install (or running a live 64-bit distro disc), it sees the onboard NIC but right away tells me I'm "disconnected".  Checking further, it identifies the nic correctly, however it never actually connects.  Tried DHCP -- never gets an IP (and yes I checked all router settings).  Manually set the IP -- can't ping anything.  But unlike the original poster, I stuck in a PCI nic and it connected right away.  If not for the additional USB issues, I would have lived with it like that.

Running a 32-bit live CD or, what I eventually did, a 32-bit install, onboard nic connects right off the bat and all USB ports work.

---

### Post by Grinage on 2013-02-02
[http://www.amd.com/us/products/embedded/develop-and-design/Pages/processor-chipset-linux-supprt.aspx](http://www.amd.com/us/products/embedded/develop-and-design/Pages/processor-chipset-linux-supprt.aspx)

I was able to find support documentation all the way up to the previous release for both 32 bit and 64 bit os kernels.  Just not this particular chipset, there's a new kernel release pending, and the updated support for the chipset will probably be with it.


There is information about 32bit linux kernels if you dig around long enough, just not 64 bit so hopefully this will be patched quickly.

---

### Post by Grinage on 2013-02-02
A thought, following up on the post about the launchpad bug for another motherboard, I remembered that there was a nightmare of updates from the install kernel version to the most current stable release in the repos.  The kernel on the installer cd doesn't have those updates.  The docs on AMD's site are only a few weeks old, the patch may have already been implemented, kernel 3.8 is in heavy testing for Unbuntu's next release I think they're on rc5 now, but 3.7.5 is available for download from the stable repositories.  This is a shot in the dark but if you download the x64 kernel packages for 3.7.5, headers and images files, burn them to a cd or put them on an external drive  install the 64 bit OS and then manually install the debs you downloaded from Ubuntu using dpkg if it installs completely it might resolve the issue.   If you've tried this or something similar post again.  For this to work you'd probably also need some library files if you're willing to try this lengthy method I'll try and post a full list of files and dependencies.

---

### Post by qwertybyrd on 2013-02-05
I am having the same problem with the NIC, but I discovered that if you plug the usb keyboard into one of the two usb3 ports on the back, the keyboard/mouse will work.

---

### Post by Grinage on 2013-02-05
If you can use a secodnary nic and get online you should be able to address the USB issue.  There also seems to be a persistent issue with the onboard nic  itself for this board for windows and linux.  Hopefully by tomorrow I'll have the completed list of packages and dependencies if you want to attempt to force an updated kernel install to see if this resolves the issues.

---

### Post by Grinage on 2013-02-07
Sorry this took so long to post, it's not just a few boards out there with these problems it's a whole bunch of them, and I've spent the past two days dealing with angry customers who upgraded to previously trusted and recommended brands.  I'll recap the issue we ran across, and the solutions and then at the end list the kernel packages.

Issue 1:  The system boots and installs normally with any 32 bit OS, but when a 64 bit OS is installed the network card no longer functions correctly or at all.  This has been seen in only intel / realtek built-in nics so far regardless of board make and model.

Solution1:  Turns out that for about a third of these the problem is that there is some sort of bug in the nic itself so that the 64 bit Linux OS identifies the built-in as eth1 instead of eth0 and the interfaces file is built by default for eth0.  Altering the file to reflect eth1 instead of eth0 resolved this 90 percent of the time.

```
sudo nano /etc/network/interfaces
```or your favorite editor as root

Issue 2:  Because of the glitch, the OS is trying to use USB2.0 slots as eth0 in some cases.

Solution2:  Disable the on board NIC in the BIOS and use a PCIe network card, this usually addresses both Issues unless you're pcie network card is the same intel / realtek card.   In around 70% of the machines I've seen, if we can get the machine on line and run all the recent updates all the USB issues have been resolved after disabling the on board NIC.  (microsoft has _several_ security patches to resolve this, you will have to download them from microsoft and install them manually for windows users)

Issue 3:  Some Boards apparently made it through production with _very_ old BIOS and many things aren't working in either windows or linux.

Solution3:  Before attempting to use your machine functionally you will have to go out to the manufacturer's website and download the latest flash and some of these are only a few days old so it seems that manufacturers are getting on the ball here, some aren't and we've had to advise these even angrier customers at this point to return their MOBO's.  If however, your board does have an update, installing it is going to be critical.    The problem is that some of these updates and flashes only work in a windows environment, and if you don't happen to have a mswindows install cd lying around or a handy windows emulated flash drive installing the updates is difficult, and installing windows so you can then erase it to install linux seems counterproductive to me, if yor're considering a dual boot system now is the time to plan it out if you have to do this.

Issue4:  Onboard Nic only functions in DHCP mode, if a static route is required it drops packets or ceases to function or some combination thereof.

Solution4:  This is due to the issues with the card itself and not configuration settings or the kernel, the only solution to this is to disable the nic and use a drop in.


As promised if you want to manually install an updated kernel after install, you will need these packages from ubuntu:
linux-headers-3.5.0-23
linux-image-generic
linux-image-3.5.0-23-generic
linux-image-extra-3.5.0-23-generic
linux-firmware
coreutils

latest version of
dpkg
libac1
libattr1
libc6
libselinux1
libpci3
zlib1g
multiarch-support
pciutils
liblzma5
tar
libbz2-1.0
libkms1
libdrm2
linux-firmware-nonfree
libapm1

You can download these as debs directly from Ubuntu, make sure you get the 64bit versions, you can then install your 64 bit OS and using a terminal browse to the location where you have the files a flash drive or cd/dvd and use

```
 sudo dpkg -i *
```to install all the packages in that location.

So far only six boards have required us to go to such an extreme, but it did allow us to get online either via PCI drop in or getting the onboard to work as eth1, dpkg may tell you that it breaks all sorts of dependencies, this is alright once you are online 

```
 apt-get update
``````
 apt-get upgrade
``` and 

```
 dpkg-reconfigure -a
```resolve almost all broken packages and it wasn't a big deal to manually fix one or two that needed extra tweaking in some cases.

On that note there have been twenty boards from various manufacturers that we couldn't do anything with at all.  There does seem to be another multitude of patches forthcoming in the next major kernel release.  That may patch around all of these issues approriately, but as far as I know it's still only in the beginning rc stages so it could be some time before the next stable kernel is released, or it could be tomorrow, I'm sure someone in the forums is keeping up with it.

I'm sure this isn't the end of this.  If other less complicated and time consuming solutions are out there Please Post!

---

### Post by monkblah on 2013-02-11
Just wanted to add to this thread in case in helps someone -- I have also been experiencing this bug (Networking and USB not working with 64-bit Linux kernels on the Gigabyte 970A-D3 Rev. 3.0 motherboard). I originally posted about it in [[COLOR="Blue"]**this thread**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=12499970") if you want gory details.

Note that my motherboard is a D3, not a DS3, though they are almost identical.

Also note my motherboard is Rev. 3.0. The Revision is important as it has a different bios than the earlier Revs; also, I did not have this problem with the earlier Rev that I used briefly.

Further note, 32-bit kernels work fine, it's only the 64-bit ones that don't have successfull Networking and USB.

And further note - the same problem exists in the current 13.04 Raging 64-bit kernel as well.

The good news: I was able to get my system working by setting IOMMU to ENABLED in the bios (it was set to disabled by 'optimized settings'/defaults).

YMMV. I figured out that I should play with this setting by going through this thread and the similar [[COLOR="Blue"]**launchpad bug**[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/859137") mentioned earlier ( []() ), though I don't know if anyone else solved it by the same method.

Not 100% sure where this bug should be reported to. Its not strictly a Ubuntu bug, it affects all 64-bit kernels (that I tried, at least). I guess it might be considered primarily a gigabyte bug. Not sure. I do feel, though, that it would be better if the kernel gave some more useful warning / debug messages in this case so people could diagnose it better. I ended up spending many hours working on this.

---

### Post by andyhelloween on 2013-02-11
> **monkblah said:**
> Note that my motherboard is a D3, not a DS3, though they are almost identical.

Thanks for this! I was going to buy that motherboard for an ubuntu server installation... keep looking now...

cheers.

---

### Post by sanderj on 2013-02-11
> **monkblah said:**
> 

Not 100% sure where this bug should be reported to. Its not strictly a Ubuntu bug, it affects all 64-bit kernels (that I tried, at least). I guess it might be considered primarily a gigabyte bug. Not sure. I do feel, though, that it would be better if the kernel gave some more useful warning / debug messages in this case so people could diagnose it better. I ended up spending many hours working on this.

I would report it on launchpad, certainly because of the 32/64-bit dependency. Because it is a kernel bug, someone will say "upstream bug".

Reporting a bug is easy: 

```

ubuntu-bug linux

```
That will collect and fill-out all your system info.

HTH

---

### Post by monkblah on 2013-02-11
Hi again Sanderj. Yeah, I've already been trying to report it on launchpad, but apport doesn't seem to want to cooperate. Posted a question about it to launchpad [[COLOR="Blue"]**here**[/COLOR]]("https://answers.launchpad.net/ubuntu/+source/apport/+question/221566").

You wouldn't happen to know if this is a known problem with apport for Live CDs or somesuch, would you?

---

### Post by qwertybyrd on 2013-02-11
An enormous thank you to monkblah - That fixed my problem in one easy step. Now to the question - why would I not want iommu enabled, even if the motherboard would work with it disabled?

---

### Post by monkblah on 2013-02-12
qwertybyrd I'm very glad this helped someone! I spent countless hours struggling with it before finally stumbling into the solution with some help on these boards. 

Now I'm having a new problem actually installing ubuntu to my hard drive. Something to do with UEFI, I think. Will probably have to start another thread...

---

### Post by 6tonspacefly on 2013-03-21
> **monkblah said:**
> The good news: I was able to get my system working by setting IOMMU to ENABLED in the bios (it was set to disabled by 'optimized settings'/defaults).

This worked for me! Thank you SO much!

---

### Post by boozer_2 on 2013-04-12
> **monkblah said:**
> Just wanted to add to this thread in case in helps someone -- I have also been experiencing this bug (Networking and USB not working with 64-bit Linux kernels on the Gigabyte 970A-D3 Rev. 3.0 motherboard). I originally posted about it in [[COLOR="Blue"]**this thread**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=12499970") if you want gory details.

The good news: I was able to get my system working by setting IOMMU to ENABLED in the bios (it was set to disabled by 'optimized settings'/defaults).



Dude... I owe you one...  I had spent hours searching and trying random bios settings... that one was down lower, so I hadn't got to it yet, was frustrated so dont know if I ever would have, lol.  I was searching mainly by motherboard model, mine is GIGABYTE GA-990FXA-UD5 

I threw that it so it hopefully pops up in someones future search and saves them time as well.

Thanks again!

---

### Post by prodriguezii on 2013-05-17
> **boozer_2 said:**
> Dude... I owe you one...  I had spent hours searching and trying random bios settings... that one was down lower, so I hadn't got to it yet, was frustrated so dont know if I ever would have, lol.  I was searching mainly by motherboard model, mine is GIGABYTE GA-990FXA-UD5 

I threw that it so it hopefully pops up in someones future search and saves them time as well.

Thanks again!
I confirm that enabling the IOMMU setting fixes USB for the GA-990FXA-UD3 Rev 3 Board. Thank you so much! Now I just need the onboard NIC to work and I'll be in heaven.

---

### Post by prodriguezii on 2013-05-17
Update: I updated my BIOS to the latest version (FC) for my board (GA-990FXA-UD3 Rev 3). I enabled IOMMU and reinstalled Ubuntu Server 12.04 64 bit. The USB and onboard NIC (Realtek 8111E) are now working. Thank you Thank you Thank you!

---

### Post by gamarino on 2013-06-08
Try seting IOMMU=yes on BIOS setup. All USBs and the onboard Ethernet should be fixed

---

### Post by ironic-destruction on 2013-08-07
:edit:
Turning on IMMOU let me use network/usb
disabling uefi allowed me to install Ubuntu
Removing a corrupt gpt on the HDD let me dual boot.

I actually have it sorted now more or less.
__

After getting this computer set-up I was having some issues with booting into Ubuntu as well, Windows 8 installed from a USB no problems.

I have the Gigabyte 970A-DS3 Rev.3 board, I got it yesterday and it already had the latest BIOS firmware (FD if I remember right).

USB/Network didn't work until I enabled IMMOU in the BIOS.

So, because I've spent all day trying to get this working, I just hit install, and everything went as I expected up until boot time.

It booted straight into Windows, I've gone into the livecd to make sure grub is installed but it just seems to ignore it no matter what I do.

Just wondering if anybody has a solution and apologies in advance if I made any errors, it's late and I'm brain-tired.

---

### Post by lah-ca on 2013-10-21
> **monkblah said:**
> 
Note that my motherboard is a D3, not a DS3, though they are almost identical.

The good news: I was able to get my system working by setting IOMMU to ENABLED in the bios (it was set to disabled by 'optimized settings'/defaults).

Thanks.  I have the GA-970A-D3 (edit/correction - 970A-D3P), as well, but with a Rev. 1 PCB.  I flashed the BIOS to F5 before installing 12.04 x64, but this did not resolve the problems, not that I was expecting it to as I did not yet know the problems existed.  I managed to work around the issues with trial and error.  What was frustrating is that problems were inconsistent.  I managed to get a cheap Acer USB keyboard and a Gygabyte mouse to work on the USB 2 ports (nothing else would work at all) and all was fine for a couple of days until I took the system down off the bench, disconnecting the keyboard and mouse.  Upon reconnecting everything, the keyboard and mouse stopped working unless I plugged them into the USB 3 ports.  USB drives were hit and miss.  Some old Kingston keys worked fine.  Some newer keys did not.  USB hard drives did not work at all.  The NIC never worked.  I had to install a old 10/100 Realtek chipset card to make a network connection.

Enabling IOMMU in the BIOS ***seems*** to have resolved the issues - fingers crossed.  One minor side effect, however, is that the system takes a few seconds longer to POST and boot now.

Hmmm... Usually I am an Asus guy.  The Gigabyte purchase was deviant behaviour on my part.  :p

Thanks again.

---

### Post by ozcyto on 2013-11-16
Enabling iommu in the bios will fix the Ethernet issue and make the usb 2.0 ports work for board GA-970A-DS3P, but usb 3.0 ports will no longer work on the back of the motherboard or from the internal 20 pin connector for the front panel.

---

### Post by ozcyto on 2013-11-18
Here is my updated fix


First enable iommu in the uefi by restarting your computer and pressing delete to enter the uefi


plug your usb mouse, keyboard and thumbdrive in usb 2 ports.


save and exit the uefi


Then In Ubuntu:


press Ctrl+Alt+T to open up a terminal 


run the following command: sudo gedit /etc/default/grub


Edit the empty quotes in this line to read: GRUB_CMDLINE_LINUX="iommu=soft"


save changes to grub and exit gedit and the terminal


Open up a new terminal with ctrl+alt+t 


run the following command: sudo update-grub


then exit the terminal using this command: exit


Restart your computer press delete to get back into the uefi


Disable iommu in bios, load optimized defaults and restart.


usb, 2.0 usb 3.0 and networking all work now in Ubuntu, and disabling iommu in bios helps prevent windows freezes that was occurring if you are running a dual boot environment. 


If the above post helps anyone I am happy.

---

### Post by robertcgagne on 2013-12-01
This seems to be working for me with Xubuntu 13.10 64 bit on with my GIGABYTE GA-970A-DS3 motherboard.  Thanks for posting!

---

### Post by DiegoBravo on 2014-01-05
> **monkblah said:**
> Just wanted to add to this thread in case in helps someone -- I have also been experiencing this bug (Networking and USB not working with 64-bit Linux kernels on the Gigabyte 970A-D3 Rev. 3.0 motherboard). I originally posted about it in [[COLOR=Blue]**this thread**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=12499970") if you want gory details.

The good news: I was able to get my system working by setting IOMMU to ENABLED in the bios (it was set to disabled by 'optimized settings'/defaults).


Hey, I just re-created my account to say thank you! My last three days were wasted trying to start my wireless card in a GA-970A-D3P (sold in Lima, Perú.)

This was weird, at first I tried with an Encore Rtl 8185 with xubuntu 13.10 32 bits without any success until I disabled the on-board wired ethernet in the bios. Then got an unstable connection, but worked fine with ndiswrapper.

Later I installed my (definitive) xubuntu 13.10 x64 and the card was recognized, the AP was detected, but it never "authenticated" (and I was using mac address based authentication, i.e. no autentication per se.) The ndiswrapper complained about bad symbols so this was not an option.

 Then I tried with a tp-link atheros 9227 and the same: the AP was detected but couldn't establish the connection. I even tried the compat-wireless with the same result, and every flag in the related modules and every option to the iwconfig command, and the crda configuration.

My next step was to try a bios update but fortunately I found your post looking for issues with the mainboard. Now with the IOMMU thing, the tp-link is working fine with its open ath9k module. Thanks again!

---

### Post by 123consulting on 2014-01-10
> **ozcyto said:**
> [COLOR=#000000]In Ubuntu:[/COLOR]

[COLOR=#000000]press alt+f2 [/COLOR]

[COLOR=#000000]run the following command: gksudo gedit /etc/default/grub[/COLOR]

[COLOR=#000000]Edit the empty quotes in this line to read: GRUB_CMDLINE_LINUX="iommu=soft"[/COLOR]

[COLOR=#000000]save changes to grub[/COLOR]

[COLOR=#000000]ctrl+alt+t to open up a terminal[/COLOR]

[COLOR=#000000]sudo update-grub[/COLOR]

[COLOR=#000000]exit[/COLOR]

[COLOR=#000000]Disable iommu in bios, load optimized defaults and restart.[/COLOR]

[COLOR=#000000]usb, 2.0 usb 3.0 and networking all work now in Ubuntu, and disabling iommu in bios helps prevent windows freezes that was occurring if you are running a dual boot environment. [/COLOR]

[COLOR=#000000]If the above post helps at least one person I am happy.[/COLOR]


Well, you certainly made ME happy! Nice one...I wish I could know to fiddle like you do! But I am even less than a noobie! hahaha Thanks again!

---

### Post by Willyweasel on 2014-01-11
Enabling iommu in the bios solved this problem for me, but I have a Gigabyte GA-970A-DS3P board.

---

### Post by mittens2 on 2014-01-30
I had same problem with a GA-970A-DS3P board, setting IOMMU to enabled worked for me too, only now my USB3 doesn't work.
With IOMMU disabled the USB3 did work, while the USB2, wireless and Ethernet did not.
With IOMMU enabled the USB2, wireless and ethernet does work, but the USB3 does not

---

### Post by Willyweasel on 2014-01-30
If you add [COLOR=#000000]GRUB_CMDLINE_LINUX="iommu=soft" [/COLOR][COLOR=#000000]to /etc/default/grub then run the command sudo update-grub in a terminal. usb 2.0, usb 3.0, and ethernet should all work. Also don't forget to disable iommu in the bios.[/COLOR]

---

### Post by greg-richards on 2014-02-06
> **ironic-destruction said:**
> :edit:
Turning on IMMOU let me use network/usb
disabling uefi allowed me to install Ubuntu
Removing a corrupt gpt on the HDD let me dual boot.

I actually have it sorted now more or less.
__

After getting this computer set-up I was having some issues with booting into Ubuntu as well, Windows 8 installed from a USB no problems.

I have the Gigabyte 970A-DS3 Rev.3 board, I got it yesterday and it already had the latest BIOS firmware (FD if I remember right).

USB/Network didn't work until I enabled IMMOU in the BIOS.

So, because I've spent all day trying to get this working, I just hit install, and everything went as I expected up until boot time.

It booted straight into Windows, I've gone into the livecd to make sure grub is installed but it just seems to ignore it no matter what I do.

Just wondering if anybody has a solution and apologies in advance if I made any errors, it's late and I'm brain-tired.



Search for fix grub in google and download and install boot-repair. It fixed both my windows, after an Ubuntu install AND Ubuntu after playing with System Repair in Windows  7 and managing to bypass the boot files

---

### Post by ozcyto on 2014-05-28
> **123consulting said:**
> Well, you certainly made ME happy! Nice one...I wish I could know to fiddle like you do! But I am even less than a noobie! hahaha Thanks again!

Im glad it helped :)

---

### Post by Victor_Magalhes on 2014-08-27
I am Brazilian and I have a motherboard GA-970A-DS3P (rev. 1.0). 
Friends, you have managed to install linux on this motherboard? 


Thank you.

---

### Post by em3raldxiii on 2014-09-01
Disabling IOMMU in my BIOS and then adding [COLOR=#008000]*GRUB_CMDLINE_LINUX="iommu=soft" *[/COLOR]to grub reduced my boot time from 57 seconds to 11 seconds.  Thank you!  

It also stopped the error message [COLOR=#ff0000]AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0016 address=0x00000000ce9f9880 flags=0x0010][/COLOR] from showing up in my dmesg log a zillion times.

It also stopped the error message [COLOR=#ff0000]audit_printk_skb: 132 callbacks suppressed[/COLOR] from adding 27 seconds to the boot time.

My total dmesg log went from 1609 lines to 1004 lines.  This has been the single most effective method of reducing boot time issues for me.  The fact that it also fixed my USB 3.0 issue (which I hadn't actually noticed because I always used my USB2.0 ports on the front of the case) is just some delicious icing on the cake.

---

### Post by em3raldxiii on 2014-09-01
Disabling IOMMU in my BIOS and then adding [COLOR=#008000]*GRUB_CMDLINE_LINUX="iommu=soft" *[/COLOR]to grub reduced my boot time from 57 seconds to 11 seconds.  Thank you!  

It also stopped the error message [COLOR=#ff0000]AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0016 address=0x00000000ce9f9880 flags=0x0010][/COLOR] from showing up in my dmesg log a zillion times.

It also stopped the error message [COLOR=#ff0000]audit_printk_skb: 132 callbacks suppressed[/COLOR] from adding 27 seconds to the boot time.

My total dmesg log went from 1609 lines to 1004 lines.  This has been the single most effective method of reducing boot time issues for me.  The fact that it also fixed my USB 3.0 issue (which I hadn't actually noticed because I always used my USB2.0 ports on the front of the case) is just some delicious icing on the cake.

---

### Post by cpare2 on 2014-11-09
> **ozcyto said:**
> Here is my updated fix

First enable iommu in the uefi by restarting your computer and pressing delete to enter the uefi
plug your usb mouse, keyboard and thumbdrive in usb 2 ports.
save and exit the uefi
Then In Ubuntu:
press Ctrl+Alt+T to open up a terminal 
run the following command: sudo gedit /etc/default/grub
Edit the empty quotes in this line to read: GRUB_CMDLINE_LINUX="iommu=soft"
save changes to grub and exit gedit and the terminal
Open up a new terminal with ctrl+alt+t 
run the following command: sudo update-grub
then exit the terminal using this command: exit
Restart your computer press delete to get back into the uefi
ENABLE iommu in BIOS.

usb, 2.0 usb 3.0 and networking all work now in Ubuntu, and disabling iommu in bios helps prevent windows freezes that was occurring if you are running a dual boot environment. 
If the above post helps anyone I am happy.

A few new items
[LIST]
[*]There is a BIOS release for this board ([mb_bios_ga-970a-ds3p_f2i]("http://www.gigabyte.us/products/product-page.aspx?pid=4591&dl=1&RWD=0#")) 10/2014, but it doesn't fix the problem.
[*]If doing a new build, change the BIOS , and simply add the grub command line to include "iommu=soft" your install will find the DHCP server, and this setting is automagically added to grub.
[*]There seems to be some inconsistency in the iommu setting - I would suggesting setting your BIOS settings back to default (lets be honest, you have dorked with all kinds of stuff before you gave in and looked for an answer online), and then change the setting to "ENABLED" - this did the trick for me.
[/LIST]

---

### Post by RobTheBold on 2015-01-08
> **ozcyto said:**
> Here is my updated fix


First enable iommu in the uefi by restarting your computer and pressing delete to enter the uefi


 . . .

This issue affects me -- and this fix fixes for me-- Trusty 64 bit and a GigaByte GA-990FXA-UD3 motherboard.

However, if, even after I've applied this fix, I boot with my HP LaserJet 1020 plugged into a USB port, problems return plus a few "bonus" issues. Booting takes 3 minutes or more and I get lots of USB enumeration failure complaints. Then no USB keyboard support, no networking, and of course the printer doesn't work.I should add that the printer had been working before I upgraded the MB using the HPLIP printer support and tools. I can also plug in the printer after booting up and logging in, without breaking keyboard, mouse and network support, but the printer isn't recognized by the driver. It *is* seen with 'lsusb'.

Nevertheless, thanks to you and everyone else who got this issue resolved. I'm going to further investigate the printer thing. I'm not totally surprised by this behavior, it is a "winprinter" after all, but it is disappointing.

---

### Post by risakcece on 2015-01-24
Hi, I'm looking for this motherboard "GIGABYTE 970A-DS3P" rev 1.0, on gigabyte website is new bios it still not fix the problem? are you recommended this board for ubuntu or is better look for other board (brand)

Thanks

---

### Post by RobTheBold on 2015-01-24
> **risakcece said:**
> Hi, I'm looking for this motherboard "GIGABYTE 970A-DS3P" rev 1.0, on gigabyte website is new bios it still not fix the problem? are you recommended this board for ubuntu or is better look for other board (brand)

Thanks

I don't think I'd recommend this MB series to a novice doing his/her own Ubuntu installation. Given that the fix requires googling the right terms to find this thread or a similar one, modifying the BIOS settings, editing a text configuration file and mucking around a little on the command line, it might sort of spoil the "it just works" experience of installing and using Ubuntu.

Obviously, the above does not apply to a more seasoned user. (Still, I'm glad I encountered the problem in the privacy of my own home on my personal PC, not installing Ubuntu for my Mom or Uncle, etc. after making a big deal -- as I tend to do -- about how easy it will be for them to use.)

---

### Post by risakcece on 2015-01-24
> **RobTheBold said:**
> I don't think I'd recommend this MB series to a novice doing his/her own Ubuntu installation. Given that the fix requires googling the right terms to find this thread or a similar one, modifying the BIOS settings, editing a text configuration file and mucking around a little on the command line, it might sort of spoil the "it just works" experience of installing and using Ubuntu.

Obviously, the above does not apply to a more seasoned user. (Still, I'm glad I encountered the problem in the privacy of my own home on my personal PC, not installing Ubuntu for my Mom or Uncle, etc. after making a big deal -- as I tend to do -- about how easy it will be for them to use.)

THX for answer, I'm not totally novice (I'm on Ubuntu for a three years) but also can't say I'm a seasoned user. It's a little disappointing gigabyte is not now more linux friendly they are made nice boards... (I haven't problem fix the issue one two times but if it doing issue again after plugged some DAC, printer or whatever) that's not for me.

I need board for AMD Athlon II X3 445 with option unlock hidden core, GIGABYTE 970A-DS3P looks like best value option but after this thread ASROCK 980DE3/U3S3 looks like better option.

---

### Post by golding on 2015-02-04
I have a new Gigabyte GA-970A-D3P Ultra Durable, however my problem seems to be a mix of the above.

I have updated the Bios to the latest and reset the Bios to Optimised and installed my OS.  During installation everything worked out of the box, in 64Bit as well.  It was when I went back to the machine afterwards and rebooted that my troubles began.

Now I have either the Networking (onboard or card) working without USB-3 ---- OR ----- I get USB-3 and NO networking depending on whether I have IOMMU enabled or disabled. So I have left the IOMMU enabled so I have connectivity and no USB-3, but I have USB 1&2.

I'm not asking for a fix, that will appear in time, beause I use Gentoo (haven't used Ubuntu for 6 yrs) and the forums are, I think, more for your own users.  This post is FYI only

---

### Post by bryan43 on 2015-02-24
Thumbs up for ozcyto.  Worked for me.

Without this IOMMU fix, no networking works.  No wireless cards (pci-e or pci) and no wired cards (built in or pci) work.  This only applied to 64bit, 32bit worked fine with IOMMU disabled.

---

### Post by Adriaan_Willem on 2015-05-16
Thanks man, i have been searching for a way to edit the ubuntu 15.04 kernel, and yous explanation, was just perfect! thanks a lot !

---

### Post by Jonathan_Niccolls on 2015-09-08
> **cpare2 said:**
> A few new items
[LIST]
[*]There is a BIOS release for this board ([mb_bios_ga-970a-ds3p_f2i]("http://www.gigabyte.us/products/product-page.aspx?pid=4591&dl=1&RWD=0#")) 10/2014, but it doesn't fix the problem.
[*]If doing a new build, change the BIOS , and simply add the grub command line to include "iommu=soft" your install will find the DHCP server, and this setting is automagically added to grub.
[*]There seems to be some inconsistency in the iommu setting - I would suggesting setting your BIOS settings back to default (lets be honest, you have dorked with all kinds of stuff before you gave in and looked for an answer online), and then change the setting to "ENABLED" - this did the trick for me.
[/LIST]

Thank you SO much for this information. I recently bought a Gigabyte 990FXA-UD3 MoBo, and an AMD FX-8370 CPU. Having this trick up my sleeve, really helps! I hope that the people that maintain the grub, can see fit to add this into the next GRUB edition, as it has completely freed up my USB 3.0 ports, as well as gotten rid of that pesky AMD Vi error that plagued my system.

---

### Post by meowsus on 2015-11-01
Can't thank the OP enough. I had been trying to figure out why my Atheros card wouldn't work for 2 days until I realized that my USB2.0 ports were also jacked up. Great post. Saved my butt.

---

### Post by Derek_Jansen on 2016-01-15
> **ozcyto said:**
> Here is my updated fix

First enable iommu in the uefi by restarting your computer and pressing delete to enter the uefi

plug your usb mouse, keyboard and thumbdrive in usb 2 ports.

save and exit the uefi

Then In Ubuntu:

press Ctrl+Alt+T to open up a terminal 

run the following command: sudo gedit /etc/default/grub

Edit the empty quotes in this line to read: GRUB_CMDLINE_LINUX="iommu=soft"

save changes to grub and exit gedit and the terminal

Open up a new terminal with ctrl+alt+t 

run the following command: sudo update-grub

then exit the terminal using this command: exit

Restart your computer press delete to get back into the uefi

Disable iommu in bios, load optimized defaults and restart.

usb, 2.0 usb 3.0 and networking all work now in Ubuntu, and disabling iommu in bios helps prevent windows freezes that was occurring if you are running a dual boot environment. 

If the above post helps anyone I am happy.

Confirmed for me.
[LIST]
[*]Ubuntu 14.04.1
[*]GA-990FXA-UD3
[/LIST]

---

### Post by asmith16 on 2016-01-21
> **ozcyto said:**
> Here is my updated fix


First enable iommu in the uefi by restarting your computer and pressing delete to enter the uefi


plug your usb mouse, keyboard and thumbdrive in usb 2 ports.


save and exit the uefi


Then In Ubuntu:


press Ctrl+Alt+T to open up a terminal 


run the following command: sudo gedit /etc/default/grub


Edit the empty quotes in this line to read: GRUB_CMDLINE_LINUX="iommu=soft"


save changes to grub and exit gedit and the terminal


Open up a new terminal with ctrl+alt+t 


run the following command: sudo update-grub


then exit the terminal using this command: exit


Restart your computer press delete to get back into the uefi


Disable iommu in bios, load optimized defaults and restart.


usb, 2.0 usb 3.0 and networking all work now in Ubuntu, and disabling iommu in bios helps prevent windows freezes that was occurring if you are running a dual boot environment. 


If the above post helps anyone I am happy.

Thank you ozcyto and everyone else who contributed to this thread! I bought the motherboard (GA-970A-D3P) without checking whether it will work with Linux, it's been so long since I've even heard of a motherboard that doesn't :) So I was pretty annoyed with this problem, but thanks to you guys it's all good now.

The solution quoted above worked for me.

Cheers!

---

### Post by phoinx on 2016-02-17
My Gigabyte GA-970A-DS3P had USB and ethernet issues too, and now it's SOLVED.
Be happy then, ozcyto! =]
Thanks everyone in this thread!

---

### Post by diazgbs on 2016-04-25
Hi Everyone, I did bought the DS3P so I have same problem " nic and USB port 2.0 Do not work" When I tried to apply this fix   (enabling **IOMMOU**) it takes a lot time and I never can see the desktop environment from live CD (Ubuntu 16.04) and I see a message related to AMD and Something.

  **is there any problem with XFX R9 390 GPU with this fix?**

NOTE: I couldn't complete this fix.

ALSO: With this fix all ports (including PCI-e, PCI) works fine?

---

### Post by bkorb on 2016-07-25
If you got here because you cannot get devices to work in a USB hub plugged into the USB port on the main board, this is to tell you that you must buy a PCI-E add on card.  The Etron Technology, Inc. EJ168 USB 3.0 Host Controller chosen by Gigabyte is second rate garbage.  Next time, buy from a company that qualifies their hardware.  Sorry.  :(

---

### Post by 2e0pgs on 2017-03-14
[B][SIZE=3]Ok so for anyone with "GIGABYTE GA-970A-DS3" I have done alot of testing and research. The best config I found to get USB3 working is this:
[/SIZE][/B]Edit Grub config:
`sudo nano /etc/default/grub`
Edit the line that looks like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Add "amd_iommu=on iommu=pt" to the end of it so now the line now looks like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amd_iommu=on iommu=pt"
Update grub:
`sudo update-grub`
once you have done that reboot the system and hit DEL / Delete key to enter BIOS/EUFI setup:
Ensure IOMMU is enabled, XHCI handoff is enabled, EHCI handoff is disabled, USB Legacy support is enabled. OS type I have set to Windows8 but I have CSM enabled "Compatibility Support Module" so Linux will boot via BIOS emulation instead of UEFI.


This fix allowed my USB3 to work properly and fixed a few audio issues.


For bonus fix if your running a x64 bit Ubuntu and find USB transfers hang at the end apply this fix:
[https://unix.stackexchange.com/questions/107703/why-is-my-pc-freezing-while-im-copying-a-file-to-a-pendrive/107722#107722](https://unix.stackexchange.com/questions/107703/why-is-my-pc-freezing-while-im-copying-a-file-to-a-pendrive/107722#107722)


This is working on Ubuntu 16.04.2, Kernel: x86_64 Linux 4.4.0-66-generic

---

### Post by thanekrios on 2017-05-17
Guys very sorry for the necrobump. I have the 970A-DS3P board and my installation freezes. I'm currently using Mint 18.1 Cinnamon but I would like to use Ubuntu. Is this a motherboard-specific problem or a more common issue?

Thanks!

---

