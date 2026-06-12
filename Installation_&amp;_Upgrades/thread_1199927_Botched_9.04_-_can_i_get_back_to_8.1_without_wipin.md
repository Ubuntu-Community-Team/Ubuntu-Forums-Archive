---
title: "Botched 9.04 - can i get back to 8.1 without wiping disk?"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by 2mayan on 2009-06-29
I've posted a thread looking for help fixing my newly upgraded DELL Inspiron .  I upgraded to 9.04 and now graphics/monitor is all hosed up.  My question now (as a novice UBUNTU  user) is whether there is an easy way to get back to the nice 8.10 version that i successfully had working a few days ago without doing a complete clean re-install of the whole disk and wiping out my harddrive.  When i boot up the computer, the only options i see at the "esc" prompt are a few variants of 9.04 and factory-settings.
Help please!!!  Much appreciated, i am totally stuck with no computer.

---

### Post by raymondh on 2009-06-29
> **2mayan said:**
> I've posted a thread looking for help fixing my newly upgraded DELL Inspiron .  I upgraded to 9.04 and now graphics/monitor is all hosed up.  My question now (as a novice UBUNTU  user) is whether there is an easy way to get back to the nice 8.10 version that i successfully had working a few days ago without doing a complete clean re-install of the whole disk and wiping out my harddrive.  When i boot up the computer, the only options i see at the "esc" prompt are a few variants of 9.04 and factory-settings.
Help please!!!  Much appreciated, i am totally stuck with no computer.


AFAIK ... **there is no downgrade option thru the network**.  What you can do is install 8.10 **OVER/UNTO** the 9.04 partition which will wipe out 9.04.

Sorry.

**_Back up your files first_**.  Make sure you know which partition 9.04 resides in (hint : EXT format).

How is your HD partitioned?  Kindly post either a screenshot of gparted or the output of

```
sudo fdsik -l
```    (small L not number 1)

Thanks.

EDIT : THIS IS NOT FOR A WUBI INSTALL

---

### Post by philcamlin on 2009-06-29
no you cant dowgreade id backup my documents and wipe :(

what did you botch ?

---

### Post by Polaris96 on 2009-06-29
damage is already done.  Backup /home and then re-inatall the system you want.  Personally, I'd try doing 9.04 over again.  Not many people are having problems with it ...

---

### Post by ajgreeny on 2009-06-29
You may just need to get the graphics up and running properly on you Dell.  What hardware does it run?  If you can't get a GUI to check in terminal use the cli and run ```
sudo lshw -C display
```and tell us, or copy if you can, the output from that.  There were problems with some graphics cards/drivers at first with jaunty, but I think updates have sorted that now, so I agree, try 9.04 again, it's the best Ubuntu version so far.

---

### Post by 2mayan on 2009-06-29
Thanks all.
The graphics card is a ATI RADEON 2400.
The computer is a DELL Inspiron.  I bought in last sept so i doubt the card is "too old" or something.
i'll try getting to the cmd prompt per your last suggestion.
What about downloading 9.04 or 8.10 on another computer to a CDROM and booting off CDROM ?  to then checkout/troubleshoot?
thoughts?

---

### Post by 2mayan on 2009-07-01
per request:  Here's a snapshot of : sudo lshw -C display
*-display UNCLAIMED     
       description: VGA compatible controller
       product: RV610 video device [Radeon HD 2400 PRO]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0

So, thanks all, i'm making some progress.  I downloaded 9.04 and 8.10 ISO's. I still can't boot up completely from 8.10 ISO despite running the checkcdrom integrity first but computer boots up just fine from 9.04 ISO so clearly something just got botched during upgrade.  I am now running from CD with 9.04 and trying to FIX botched install.
Any suggestions for using the 9.04 cd to FIX the install or do i just re-install from scratch from the cd?
I still love Ubuntu and won't go back to BillGates and Office/Windows unless this thing spontaneously bursts into flames.
thanks all

---

### Post by ajgreeny on 2009-07-01
I note that at the moment you are using a live CD of 9.04, so it is obviously possible to get your system running OK with jaunty, and it seems odd still that the install just goes to a cli.  Try booting to recovery mode (second option in the grub menu) and run the **xfix** when that menu appears, as it sounds like a graphics problem to me, and this may just fix it for you.

Your "internet settings" depending on what you mean by that could be in **~/.mozilla** folder and your emails in either **~/.mozilla-thunderbird** or **~/.evolution**, it depends which email client you use, obviously.  If you mean your network settings to actually get online, I don't know where they are stored, but if your hardware is supported, it should not be a long job to get that up and running from scratch.  Open Office details are all in the hidden folder **~/.openoffice.org**.

Al the other configuration is in a number of other folders, in both your home, and also for some applications in /etc and other filesystem folders, but I never bother with those and always start again from scratch when I upgrade ubuntu versions.  I hope that all helps.

---

