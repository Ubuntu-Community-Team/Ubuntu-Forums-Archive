---
title: "How can i dualup with a modem?"
date: 2007-04-12
forum: Hardware &amp; Laptops
---

### Post by exidez on 2007-04-12
i dont know how to dialup via a modem. it said in the help that modem drivers were not installed and told me to find out what chipset it is but i dont know what to do from there.
i cannot find any linux drivers

here is my modem details:
what can i do?


--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 6.10 
Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
 scanModem update of:  2007_March_15


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:2668	1854:0014	Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW 

 Modem interrupt assignment and sharing: 
169:      10893   IO-APIC-level  uhci_hcd:usb4, ohci1394, HDA Intel, yenta, radeon@pci:0000:01:00.0

 --- Bootup diagnositcs for card in PCI slot 00:1b.0 ----
[17179592.920000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179592.920000] PCI: Setting latency timer of device 0000:00:1b.0 to 64

 === Finished modem firmware and bootup diagnostics section. ===

---

### Post by klytu on 2007-04-14
Please post the output of: ```
sudo wvdialconf /etc/wvdial.conf

``` 
II'll try to help...

---

### Post by Chappy7777 on 2007-04-14
Do yourself a favor and get an External Serial Modem. I finally did, and as soon as I plugged it into my PCs serial port, it was detected and I was online upgrading Firefox.

Read some of the posts at the Networking and Wireless Forum. Maybe post your question there as well.

God bless,
Chappy

---

### Post by Whatawonderfulday on 2007-04-15
Perhaps I can shed a little light.

I'm not too sure about the status of a USB modem, but the following obtains for built-in modems and pcmcia card modems.  Starting with kernel 2.6.14, I believe, there was a regression in the kernel so that such modems were not properly handled and it was impossible to set up a modem at all (at least of the types specified).  Someone told me that the problem had been sorted out in the 2.6.20 kernel and to wait for that kernel to circulate (in the particular discussion that I had, in Fedora Core--I assume that the fix would appear in any Linux kernel labelled 2.6.20, although I have been trying without success to verify this).  The 2.6.20 kernel is now circulating, but in the case of Ubuntu from what I have just seen in the forum, to use that kernel with edgy eft you would have to do a compile, not a trivial matter; otherwise you have to get feisty fawn, which comes 'out of the box' with a version of the 2.6.20 kernel.  So as things stand, at least for built-in modems and pcmcia modems such as 3COM 3CXEM556 B, you have to upgrade to feisty fawn.  However, I emphasize that I have been unable to get anyone to confirm that the fix for modems has indeed been installed in the 2.6.20 kernel as it appears in feisty fawn.  It seems that unless someone clarifies this (please!) it will be necessary to upgrade to feisty fawn using a network or similar and then go off to a telephone to try the modem to see what happens.

Moreover, part of the reason for the regression is that the code for handling modems was moved into the kernel from external drivers.  Hence, with any of the kernels between 2.6.14 and 2.6.20 inclusive, the modem is not properly detected and you are wasting your time with wvdial.  Of course if someone was able to use an external modem on his serial port, that is another matter.

Hope this helps.  I sure would appreciate it if one of the techies would clarify this.

Whatawonderfulday.

---

### Post by Chappy7777 on 2007-04-15
Can you please clarify your post for someone who gets lost in all the numbers? Are you saying that as of Feisty Fawn we will be able to use winmodems to connect via dialup (my only choice being dialup, this would be great). I'm not as dumb as this question sounds, just real new to Linux.  

Chappy

---

### Post by Whatawonderfulday on 2007-04-15
Dear Chappy7777:

It's not a dumb question.  As far as I know, whatever you could do prior to kernel 2.6.14 with a modem, you can again do once you have a Linux distro installed that has kernel 2.6.20.  In the case of Ubuntu this means Feisty Fawn.  This is the theory.  The practice I would love to confirm with an Ubuntu techie: does the kernel in Feisty Fawn contain the fixes for dial-up modems?

The situation prior to 2.6.14 was that you had to install drivers which would work with your inbuilt modem.  This was a big problem because you had to search around for proper drivers for your particular modem.  Moreover, most inbuilt modems are now 'soft modems', which means that they are implemented in large proportion in software tailored to Windows.  This presents serious problems with Linux.  One solution is to use a pcmcia modem (which in any event has better performance in case you have an inferior line), where the drivers are already installed in Linux.  The only problem I had in Fedora Core 4 was configuring the pcmcia modem.  That required an expert's assistance.  I didn't use the inbuilt soft modem not because I couldn't find drivers but because I have a bad line and therefore lousy performance with the inbuilt modem.

When I upgraded FC4 and found myself with a new kernel, I found that I no longer could use any modem at all, because the Linux OS no longer DETECTED the modem.  This was because of changes to the kernel.  Fortunately the upgrade to FC4 gave me the option to use the old kernel, which continued to support the modem.  This problem with the kernel continued with FC6.  I did some informal inquiry and was told by a systems engineer who had occupied himself with the problem that the problem was fixed in kernel 2.6.20, and to wait for that kernel to be issued (in the event, for Fedora).  In the meantime other unrelated problems with Fedora led me to Ubuntu.  I installed Ubuntu 6.10 knowing that I wouldn't be able to use the modem and have been trying to find out where kernel 2.6.20 fits into the Ubuntu picture.  The answer is that it is the shipped kernel with Feisty Fawn.

Now the big question is: have the fixes been put into the shipped Feisty Fawn kernel?  I sure would like to find out.

Now for the particular problem that you have.  Modems are a very complicated matter in Linux.  At present (prior to kernel 2.6.20)  the kernel does not detect, as far as I know, any modem.  There's a bug in the kernel having to do with bringing modem management functions from external drivers into the kernel.  However, whether you are going to be able to use a soft modem with Feisty Fawn...  Well, I really don't know.  You might still have to find special drivers.  Then again, you might not.  If a kernel expert could enter into the discussion to explain all of this, then I would learn some things myself.

Sorry, that's the best I can do.

Whatawonderfulday

---

### Post by Cariboo1938 on 2007-04-15
> **exidez said:**
> i dont know how to dialup via a modem. it said in the help that modem drivers were not installed and told me to find out what chipset it is but i dont know what to do from there.
i cannot find any linux drivers
what can i do?

Before you do anything else follow "klytu's" advice and post the output of:
Code: sudo wvdialconf /etc/wvdial.conf (open a terminal and copy/paste the code)
It will tell you if your modem is detected at all. Among others, you should get text lines similar to this:
> ttyS2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS2<*1>: Modem Identifier: ATI -- TP560 Data/Fax/Voice 56K Modem
ttyS2<*1>: Speed 4800: AT -- OK
Good Luck

---

### Post by klytu on 2007-04-15
> **Whatawonderfulday said:**
> Dear Chappy7777:

It's not a dumb question.  As far as I know, whatever you could do prior to kernel 2.6.14 with a modem, you can again do once you have a Linux distro installed that has kernel 2.6.20.  In the case of Ubuntu this means Feisty Fawn.  This is the theory.  The practice I would love to confirm with an Ubuntu techie: does the kernel in Feisty Fawn contain the fixes for dial-up modems?

The situation prior to 2.6.14 was that you had to install drivers which would work with your inbuilt modem.  This was a big problem because you had to search around for proper drivers for your particular modem.  Moreover, most inbuilt modems are now 'soft modems', which means that they are implemented in large proportion in software tailored to Windows.  This presents serious problems with Linux.  One solution is to use a pcmcia modem (which in any event has better performance in case you have an inferior line), where the drivers are already installed in Linux.  The only problem I had in Fedora Core 4 was configuring the pcmcia modem.  That required an expert's assistance.  I didn't use the inbuilt soft modem not because I couldn't find drivers but because I have a bad line and therefore lousy performance with the inbuilt modem.

When I upgraded FC4 and found myself with a new kernel, I found that I no longer could use any modem at all, because the Linux OS no longer DETECTED the modem.  This was because of changes to the kernel.  Fortunately the upgrade to FC4 gave me the option to use the old kernel, which continued to support the modem.  This problem with the kernel continued with FC6.  I did some informal inquiry and was told by a systems engineer who had occupied himself with the problem that the problem was fixed in kernel 2.6.20, and to wait for that kernel to be issued (in the event, for Fedora).  In the meantime other unrelated problems with Fedora led me to Ubuntu.  I installed Ubuntu 6.10 knowing that I wouldn't be able to use the modem and have been trying to find out where kernel 2.6.20 fits into the Ubuntu picture.  The answer is that it is the shipped kernel with Feisty Fawn.

Now the big question is: have the fixes been put into the shipped Feisty Fawn kernel?  I sure would like to find out.

Now for the particular problem that you have.  Modems are a very complicated matter in Linux.  At present (prior to kernel 2.6.20)  the kernel does not detect, as far as I know, any modem.  There's a bug in the kernel having to do with bringing modem management functions from external drivers into the kernel.  However, whether you are going to be able to use a soft modem with Feisty Fawn...  Well, I really don't know.  You might still have to find special drivers.  Then again, you might not.  If a kernel expert could enter into the discussion to explain all of this, then I would learn some things myself.

Sorry, that's the best I can do.

Whatawonderfulday

If everything you wrote is correct (I haven't researched it yet to know for myself), then I would have to report that even if the kernel doesn't detect the modem it might be usable. I have used an internal modem for the last two years through all of the kernel updates you mentioned, although it's not a software modem. The only difficulty I had occurred [COLOR="Red"]**_[[COLOR="Red"]when I inadvertently caused an IRQ conflict by changing a BIOS setting[/COLOR]]("http://ubuntuforums.org/showthread.php?t=409423")_**[/COLOR].

---

### Post by Chappy7777 on 2007-04-15
Thnx Wday,
I am using 6.06 because of the autodetect button found in the Networking/Modem/Properties box. That feature, autodetect, is not there in 6.10  I don't know all the techie Linux talk yet, or any type in command lines, but I am pretty good at common sense stuff. I am gunna stick w/6.06 until I hear different. This says to me that the kernel change happened between 6.06 and 6.10 (or is it just the autodetect of modem that's missing?) I am aware that modems built for MS won't work on Linux w/out alot of driver hunting and God's blessings. What is a PCMCIA modem? Is that for a Laptop? I am using a desktop PC. Old, antigue.
Thnx, Chappy

---

### Post by Whatawonderfulday on 2007-04-16
First, to Chappy7777:

I don't recall an autodetect button on FC4 or even later, so I can't speak to the issue of its presence or absence.

A pcmcia modem is a hard modem implemented on a pcmcia card.  A pcmcia card is a thick 'credit card' with a lot of connector holes on one end that fits into a slot on a laptop, although I see no reason for there not to be a pcmcia slot on a desktop.  If you have ever used WiFi (wireless LAN) with a laptop that did not have WiFi built in, then you would have had to go to a local store to buy a WiFi pcmcia card that fit into the same slot on your laptop.  You take one card out, you put another card in.  Under Windows, they are automatically detected as new hardware, although a WiFi card usually requires you first to run an installation disk for the special drivers.  Well a pcmcia modem is much the same thing, but doing a different job.  In the particular case of my pcmcia modem, its a 3COM pcmcia card that contains a 10MB ethernet adapter for a LAN line (not wireless) and also a hard modem.  A hard modem is one that is implemented in circuits not in software.  What you have been calling a winmodem is what I have been calling a soft modem: the inbuilt modem that ships with a laptop that contains a basic modem, but most of whose functions are implemented in software.  In the particular case of my laptop, the winmodem could be adapted to Linux, and we did, but the line I have is lousy and has special, unusual characteristics that made the software error control insist on a very low line speed on connection.  This was surpassed with the pcmcia hard modem.

I really don't know what kernel shipped with Ubuntu 6.06.  I have observed that Fedora Core and Ubuntu have a certain parallelism as regards the kernel, as is only natural since they are distros not completely different operating systems.  FC4 out of the box had kernel 2.6.13 and upgraded to kernel 2.6.17.  I do know that Ubuntu 6.10 ships with kernel 2.6.17, so it is not out of the question that you have kernel 2.6.13.  You could run a command to check, but I don't have it at my fingertips to tell you.

Next to Klytu:

I am glad that your modem is working, Klytu.  I am an old man who has many things to do.  I am not posting to this forum to waste my time.  I need to get some information.  While I once worked as a computer programmer, that was many years ago.  I am rather new to Linux and do not know all its technical details.

When I originally installed Linux, I worked with a Professor of Physics who was an expert on adapting winmodems to Linux.  We got the modem working after a lot of problems, but just barely because of my lousy line.  The Professor consulted with a modem driver programmer to sort the thing out.  The final conclusion was that I was going to get nowhere with a winmodem because of the line.  I got a pcmcia modem that worked fine under kernel 2.6.13 in FC4, but stopped working in the FC4 ugrade when I booted with kernel 2.6.17.  I had the choice of the two kernels after the ugrade.   I didn't test the inbuilt winmodem because of the lousy line.  I got hold of FC6, upgraded to that, and the modem still wasn't working.  I started to investigate why.

I corresponded with a software programmer, sending him the output of cardctl and, I think, wvdialconf.  I have the correspondence, but why should I go pull it out and cut and paste?  He flatly remarked that the output was nonsense, that there was a regression in the kernel and that I should post a bug report.  While investigating how to do that, I came across a PhD systems engineer who had the same problem with the same pcmcia modem.  Such people exist.  I corresponded with him and he told me that the problem was fixed as of kernel 2.6.20 and that I should wait for that kernel.  In the meantime other problems with Fedora Core (other hardware was not being handled properly) led to to Ubuntu.  I installed Edgy Eft 6.10 and was quite impressed with it in comparison to Fedora Core.  It handled my other hardware well.  But I knew that I wouldn't have a connection through my pcmcia modem under Linux until I installed kernel 2.6.20.  So I have been trying to confirm how I can get that kernel--and to confirm whether the fixes are actually there.  A kernel expert would know and I certainly would want to encourage someone reading this who knows a kernel expert to make an inquiry.

As far as I know, the easiest way to get kernel 2.6.20 is to install Feisty Fawn--if the fixes are there.  Installing kernel 2.6.20 with Edgy Eft would require a compile, not a trivial matter for an old man new to Linux.  I am a little nervous about installing Feisty Fawn even when it goes official because it seems a tad unstable.

If you can help sort this problem out, Klytu, I would be much obliged to you.

With best wishes--

Whatawonderfulday

---

### Post by klytu on 2007-04-16
> **Whatawonderfulday said:**
> Next to Klytu:

I am glad that your modem is working, Klytu.  I am an old man who has many things to do.  I am not posting to this forum to waste my time.  I need to get some information.  While I once worked as a computer programmer, that was many years ago.  I am rather new to Linux and do not know all its technical details.

When I originally installed Linux, I worked with a Professor of Physics who was an expert on adapting winmodems to Linux.  We got the modem working after a lot of problems, but just barely because of my lousy line.  The Professor consulted with a modem driver programmer to sort the thing out.  The final conclusion was that I was going to get nowhere with a winmodem because of the line.  I got a pcmcia modem that worked fine under kernel 2.6.13 in FC4, but stopped working in the FC4 ugrade when I booted with kernel 2.6.17.  I had the choice of the two kernels after the ugrade.   I didn't test the inbuilt winmodem because of the lousy line.  I got hold of FC6, upgraded to that, and the modem still wasn't working.  I started to investigate why.

I corresponded with a software programmer, sending him the output of cardctl and, I think, wvdialconf.  I have the correspondence, but why should I go pull it out and cut and paste?  He flatly remarked that the output was nonsense, that there was a regression in the kernel and that I should post a bug report.  While investigating how to do that, I came across a PhD systems engineer who had the same problem with the same pcmcia modem.  Such people exist.  I corresponded with him and he told me that the problem was fixed as of kernel 2.6.20 and that I should wait for that kernel.  In the meantime other problems with Fedora Core (other hardware was not being handled properly) led to to Ubuntu.  I installed Edgy Eft 6.10 and was quite impressed with it in comparison to Fedora Core.  It handled my other hardware well.  But I knew that I wouldn't have a connection through my pcmcia modem under Linux until I installed kernel 2.6.20.  So I have been trying to confirm how I can get that kernel--and to confirm whether the fixes are actually there.  A kernel expert would know and I certainly would want to encourage someone reading this who knows a kernel expert to make an inquiry.

As far as I know, the easiest way to get kernel 2.6.20 is to install Feisty Fawn--if the fixes are there.  Installing kernel 2.6.20 with Edgy Eft would require a compile, not a trivial matter for an old man new to Linux.  I am a little nervous about installing Feisty Fawn even when it goes official because it seems a tad unstable.

If you can help sort this problem out, Klytu, I would be much obliged to you.

With best wishes--

Whatawonderfulday

My suggestion for trying to use wvdial to detect the modem was directed to the original poster, who hasn't responded yet. The point of my response to your comment is that although many people have difficulty using their modems and getting them set up, there are also many who do have modems working. If you have tried several techniques (including the one I suggested), have thoroughly researched and failed to solve your problem, then yes it might be better for you wait to try the 2.6.20 kernel to see if you have better support for your hardware. The original poster may not have tried anything beyond  what they posted and I see no particular reason for them to give up or get discouraged yet if they haven't tried techniques that have helped some others.

---

### Post by Whatawonderfulday on 2007-04-16
To all:

I have received confirmation as follows:

"I see that kernel 2.6.20 is circulating.  Could you confirm that it contains the fix for this pcmcia card
problem?..."

"yes, it works fine in FC6 since kernel 2.6.20-1.2925.fc6
"see [https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=207910](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=207910)
...

"I see that Ubuntu is distributing kernel 2.6.20 and I assume that any distro which has a kernel labelled 2.6.20 has the fix installed.  Is this a reasonable assumption?"

"yes, it's been fixed in 2.6.20-rc1 according to
"[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/52510](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/52510)"

Now in Ubuntu this fixes the pcmcia modem problem with the kernel recognizing the pcmcia card as of Feisty Fawn.  Just precisely what happens with an inbuilt winmodem, I cannot say, but it is clear from reading the two bug reports (by different parties) that the problem was with the pcmcia modem.  It doesn't appear to me to have been a problem with all modems.  Hence, Klytu is at least partially right and gets my apologies for my nonsensical answer.

With best wishes--

Whatawonderfulday

---

### Post by exidez on 2007-04-17
> **klytu said:**
> Please post the output of: ```
sudo wvdialconf /etc/wvdial.conf

``` 
II'll try to help...

ok i did that and it said that no modem was detected (i saved what it said on my flash drive but i forgot to bring it to work. I have no internet access at the moment)

So, what this thread is saying is that i should update my lernal and this will resolve my probelm (eg, it will install the modem and work perfectly)?

excuse my newbieness.

---

### Post by Whatawonderfulday on 2007-04-18
To Exidez:

Since I introduced the idea of upgrading the kernel, let me clarify.  The kernel problem that I was addressing was a specific bug related to the use of a pcmcia modem.  It appears that you are using an inbuilt modem, so I really don't know if your problem would be solved by using the 2.6.20 kernel.  I apologize for the confusion.

Whatawonderfulday

---

### Post by exidez on 2007-04-18
i thought that would be the case actually..

anyway back to the origional question...
Which driver do i need to install the modem?
the list of the modem chipset drivers are here [http://www.intel.com/design/modems/support/drivers.htm](http://www.intel.com/design/modems/support/drivers.htm)
but which one is mine?

is "Intel Corporation 82801FB/FBM/FR/FW/FRW" the chipset for my modem??? as stated in the first post?

---

### Post by klytu on 2007-04-18
> **exidez said:**
> i thought that would be the case actually..

anyway back to the origional question...
Which driver do i need to install the modem?
the list of the modem chipset drivers are here [http://www.intel.com/design/modems/support/drivers.htm](http://www.intel.com/design/modems/support/drivers.htm)
but which one is mine?

is "Intel Corporation 82801FB/FBM/FR/FW/FRW" the chipset for my modem??? as stated in the first post?

This > 8086:2668 1854:0014 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW corresponds to an AC '97 high definition audio controller, which probably includes your (software-driven) modem on the card. I wasn't sure when I first looked at the output; it might have been just your soundcard. That is why I suggested you try the wvdial command first. There are a number of possible specific chipsets that could correspond to that output. I would suggest that you visit the [COLOR="Red"]_[[COLOR="Red"]Linmodems Support Page[/COLOR]]("http://132.68.73.235/linmodems/index.html#details")_[/COLOR] and forward a copy of the  ModemData.txt generated by scanModem to their discussion list for further assistance in figuring out the specific one. If you know your way around the inside of your computer, you could try opening up the box and physically inspecting the card for information.

---

