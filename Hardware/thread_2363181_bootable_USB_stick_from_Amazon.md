---
title: "bootable USB stick from Amazon"
date: 2017-06-07
forum: Hardware
---

### Post by linux28 on 2017-06-07
Hello

I am having difficulties creating a bootable usb stick for ubuntu and I was therefore thinking of buying one on amazon, How safe are they ? Can the sellers install spywares etc on them ?

Thanks in advance :)

---

### Post by howefield on 2017-06-07
Perhaps you could describe the difficulties that you are having with your existing USB sticks, where in the process of creating the Live media are you getting stuck ?

---

### Post by linux28 on 2017-06-07
Hello

basically the usb is not recognised on the boot menu.

---

### Post by TheFu on 2017-06-07
You cannot just copy over an ISO file to a flash drive.  It has to be correctly "installed" using a tool.

Ubuntu ISOs are able to boot both UEFI and legacy BIOS systems.
If you are running an UEFI system, then use something like Rufus.
If you are running a legacy BIOS system, then use something like Yumi or MultiBootUSB.

Rufus and Yumi are Windows programs.  MultiBootUSB is Linux, but I've never seen it work.

Or you can use dd, ddrescue to shove the ISO file onto a flash drive.  When I need it quick and can't be bothered to find a Windows systems, this is the method I use. It works, but is no-frills.  

As for how safe is anything from amazon, it depends on the seller. Amazon isn't the only seller on amazon.com.  It has become more like ebay with hundreds/thousands of sellers, each with a different reputation AND different return policy. I have purchased flash media from amazon in the last year and didn't have any issues (yet) - don't remember the exact vendors used. Sorry.

However, since the amount of storage needed for any Linux live-boot ISO is under 2G, I usually try to use free 8G flash drives from Microcenter for this task.  When I purchase a flash drive, it is 32G or 64G in size.  I avoid the 128+G flash drives so that exFAT isn't required.  None of my larger flash media is used for these multi-boot needs.

Please search the forums for flash/thumb drive and USB port issues too. Not all will work with every combination. Some systems are picky.

---

### Post by linux28 on 2017-06-07
[FONT=arial]thank you so much for your reply. as far as the usb stick is concerned i was talking about sticks with linux distro pre installed on them ready to boot and install, not sure if you thought that's what I meant :)[/FONT]

---

### Post by TheFu on 2017-06-07
> **linux28 said:**
> [FONT=arial]thank you so much for your reply. as far as the usb stick is concerned i was talking about sticks with linux distro pre installed on them ready to boot and install, not sure if you thought that's what I meant :)[/FONT]

I've had issues with SuSE USB sticks that were swag at Linux conferences not booting.  I spoke with the team who was handing them out. They were using an imaging tool and the specific stick they handed me worked perfectly on other machines, but not on mine.

2 issues are possible
* UEFI vs BIOS booting setup
* picky USB ports/chips and sometimes firmware issues that prevents some flash drives from working in some computers

A short story.
I have a chromebook.  Replaced googles firmware with a popular replacement about 18 months ago so I could boot directly into Linux instead (needed control over kernel modules).  That firmware only supports booting "legacy BIOS" and only from the left-hand USB2 port.  No UEFI flash boot disks worked.  Last weekend, I wanted to replace the SSD in the chromebook from a 64G to a 128G.  Mirrored everything over, but it refused to boot - which was strange, since I do this all the time with HDDs.  Actually did it about a month ago on a HDD on another machine and I'm not exactly a noob with Linux (started in 1993).  Anyway, nothing worked, so I looked for detailed steps specific to the chromebook and discovered there was a newer, different UEFI firmware available. UEFI is something I've avoided all this time, but I already had a non-working system and multiple backups, so there wasn't a better time to try something new.  Got and installed the new firmware - it went perfectly.  Then I tried to find the legacy BIOS boot option. I'd never heard of any UEFI not supporting legacy BIOS booting before.  Until last Saturday.  It won't boot using non-UEFI methods, period.  That meant all my Yumi flash drives wouldn't work.  But if I used a mix-mode or UEFI-only flash setup, then it worked.  Further, I was able to boot from the right-hand side USB3 port!!!  That just changed everything with my system and travel plans. I could place a show-and-tell OS on the machine, but keep my real OS on a fast USB3 flash drive.  At some point, I hope to get dual booting working with 2 Linuxen boots:
a) show and tell 15G Linux (for anyone who wants to see the system boot or play with Linux quickly)
b) fully encrypted install (I'm using 'b' today).

I can go on, but not sure that will actually help.

Just make your own flash drive with whatever ISO you want. There are thousands of how-to guides in the internet and youtube (if you prefer to see someone do it).  It is very important that you know whether your system is UEFI or not if you don't use official Ubuntu  flavors.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) are the ubuntu dvd instructions. Or 
Flash drive [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
 might be helpful.

---

### Post by linux28 on 2017-06-07
thanks for taking the time to answer :)

---

### Post by TheFu on 2017-06-07
DVD [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) or 
Flash drive [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
 might be helpful.

---

### Post by SeijiSensei on 2017-06-07
Use Rufus as described in the "FromUSBStick" document TheFu cites above.  It works on machines with UEFI BIOSes as well as the older standard.

If you have a bootable device, but the machine doesn't boot from it, you probably need to change the order of boot devices in the system BIOS.  You can often do this on the fly at boot by hitting a specific key, or you can change the order in the BIOS settings themselves.  Consult your system's documentation for details.

---

