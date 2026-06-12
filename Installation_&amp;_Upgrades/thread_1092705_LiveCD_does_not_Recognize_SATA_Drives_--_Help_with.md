---
title: "LiveCD does not Recognize SATA Drives -- Help with dmesg"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by f00b on 2009-03-10
Hi All,

My LiveCD (8.10 downloaded and burned yesterday) does not recognize my SATA Hard drive on an attempt to boot from the CD.  I have been reading the forums and have seen that others have had this problem as well.  I can't find anyone with the same error messages as me, or maybe I am not searching on the right criteria.  

Either way, it seems I will be able to shed more light on my specific situation if I can successfully output the error messages using the 'dmesg' command.  How can I do this since I am trying to boot from the LiveCD?  I don't see a command prompt for input...

If it helps my computer is:

Acer Aspire
Model: AM3641
Chipset: Nvidia Nforce 630i 
Hard Drive: WDC 500GB

I am running windows xp as my only operating system on the HDD.  The HDD is formatted NTFS all the way through.

I hope I have been descriptive enough.

Thank you

---

### Post by Neo_The_User on 2009-03-10
via terminal is where you do dmesg

---

### Post by taurus on 2009-03-10
Applications -> Accessories -> Terminal

---

### Post by Neo_The_User on 2009-03-10
> **taurus said:**
> Applications -> Accessories -> Terminal

That's what I said.

---

### Post by taurus on 2009-03-10
> **Neo_The_User said:**
> That's what I said.

And how does a newbie know where a terminal is if you don't point directly to it?

---

### Post by Neo_The_User on 2009-03-10
> **taurus said:**
> And how does a newbie know where a terminal is if you don't point directly to it?

lol! true. very true.

---

### Post by f00b on 2009-03-10
Ok, sorry guys.  Guess I wasn't clear enough... 

I have installed Ubuntu before so I'm not all that newbie... :-) 

just on this computer it seems to be quite a hassle... So I guess it is important to note that I am not able to get to the LiveCD ubuntu desktop, so going to the Applications menu is not an option.

Also worth noting is that I cannot boot due to a timer error looking something like this:

MP-BIOS bug : 8254 Timer not connected to IO-APIC
Kernel panic - not syncing: ... timer does not work!

... The liveCD never got past this error message and would hang before ever booting to the Ubuntu Desktop.

After i researched a bit I got by this error by pulling up the booting options with F6 at the first boot screen and then removing the 'quiet splash' option and entering the string 'noapic nolapic' instead.  This gives a very verbose system of checks before the system finally hangs at what looks like the 6th or 7th SATA hard drive check in a row.  

After more research I saw that many people seemingly having the same problem were using the dmesg command to output these errors so others could help them diagnose the real problem.

So I was hoping someone could help me figure out how to output the error log to somewhere so I can paste it here and find out my true problem.

I do have the option of plugging in a flash drive to a USB port as it seems these were recognized by the messages... so maybe using grep to output the log file to a plugged in USB drive??? Or if there is a better way I am all ears.

Thanks.

---

### Post by Neo_The_User on 2009-03-10
dmesg | grep sata
then do
dmesg | grep usb

---

### Post by f00b on 2009-03-10
> **Neo_The_User said:**
> dmesg | grep sata
then do
dmesg | grep usb

Where?  I can't type anything while it is booting?  Again it hangs on bootup...

Do I do the same steps of hitting F6
Removing quiet splash
adding noapic nolapic

And then at the end of that line type 'dmesg | grep sata dmesg | grep usb' ???

Sorry if this is painful, I guess I am more newbie than I thought :-)

---

### Post by Neo_The_User on 2009-03-10
I don't really know how to dumb this down any further no offense.

---

### Post by f00b on 2009-03-10
Ok, maybe I am using the wrong language.

These are my steps:

Put the disk in
boot from CD
Ubuntu asks what language
I select english
What I am going to call a boot menu is comes up
I have several choices
I highlight 'Try Ubuntu without an change to your computer'
I press F6 and edit the string as mentioned before
Press enter.
.....
Several Messages go by on the screen as the system attempts to boot to the live cd screen... 

It hangs and never gets past what I think is the SATA HD check... either way, I cannot get to the terminal.

So... sorry if this sounds stupid, but where do I enter 'dmesg' command?

---

### Post by Neo_The_User on 2009-03-10
Wait a sec, if you can't get to Terminal, why did me and Taurus both think that???

---

### Post by f00b on 2009-03-10
> **Neo_The_User said:**
> Wait a sec, if you can't get to Terminal, why did me and Taurus both think that???

I'm sorry.  Like I said, maybe my language was wrong.  I thought I was being pretty clear that I never got to the desktop, and specified I could not use the terminal.

Either way, this is the "Install & Upgrades" for issues and questions with installing.  Am I in the wrong forum?

If I could get the OS to install I could easily operate in the terminal.  ;-)   Like I said, ***_it hangs on bootup._***.  Unless I should be using some other terminology.

---

### Post by Neo_The_User on 2009-03-10
> **f00b said:**
> I'm sorry.  Like I said, maybe my language was wrong.  I thought I was being pretty clear that I never got to the desktop, and specified I could not use the termina.

Either way, this is the "Install & Upgrades" for issues and questions with installing.  Am I in the wrong forum?

If I could get the OS to install I could easily operate in the terminal.  ;-)   Like I said, ***_it hangs on bootup._***

nah you're on the right forum. nobody has answers. my answer: check to see if the SATA drive works in anything

---

### Post by avtolle on 2009-03-10
OK, add this to your boot options: nosplash. This will scroll the various system messages as the boot process commences and (hopefully) continues, to get you some idea of where the problem is. If you are correct that the process hangs at the SATA check, you should (IMO) then try on reboot as another boot option (making four in all) all_generic_ide to hopefully get you past that stage. Good luck.

---

### Post by f00b on 2009-03-10
It works in windows XP.  It is shared on a network and all computers on the network can access it.

The funny thing is I have gotten this computer to boot to the LiveCD desktop a 2 or 3 weeks ago. I just didn't install it that time.  Now I can't get anything to work for me.. :-(

There is no way to grep the output from the bootup messages to a thumb drive while booting up?  If all else fails I am going to type out the error because I want this to work.

---

### Post by avtolle on 2009-03-10
I don't know of any way to get the error messages to a usb drive on boot up from the Live CD given the issues that you are encountering. Hopefully, there is an answer to that in someone else's "bag of tricks".

---

### Post by f00b on 2009-03-10
> **avtolle said:**
> OK, add this to your boot options: nosplash. This will scroll the various system messages as the boot process commences and (hopefully) continues, to get you some idea of where the problem is. If you are correct that the process hangs at the SATA check, you should (IMO) then try on reboot as another boot option (making four in all) all_generic_ide to hopefully get you past that stage. Good luck.

Thanks for all the responses so far.

Ok, I tried it using the three options 'noapic nolapic nosplash'  and it hangs with this error message

[ 97.123245] scsi6 : pata_amd
[ 97.123245] scsi7 : pata_amd
[ 97.125494] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[ 97.125547] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15

Now I am going to try with all_generic_ide and get back to you.

---

### Post by f00b on 2009-03-10
With the boot option all_generic_ide I got past the error.  

Now it hangs on 

[ 102.101170] sd 6:0:0:3: [sdd] Attached SCSI Removal Disk

I don't have anything plugged in besides a keyboard mouse and monitor and ethernet cable.

Besides google, is there somewhere I can look up these messages so I can stop bothering everyone?

---

### Post by avtolle on 2009-03-10
No idea where to check on the meaning of said messages. You have attached to the computer the keyboard, mouse, monitor and Cat V cable, as I understand it, so I'm currently at a loss as to what to suggest to you next. Will ponder a bit, and if I'm able to come up with anything, will post back.

---

### Post by avtolle on 2009-03-10
Dumb question: you don't have your flash drive still attached by any chance?

---

### Post by f00b on 2009-03-10
> **avtolle said:**
> Dumb question: you don't have your flash drive still attached by any chance?

Nope, that's why I mentioned the only things I had attached.

---

### Post by f00b on 2009-03-11
... i am still stuck on this error... anybody ?

---

### Post by Neo_The_User on 2009-03-11
Negative. Do not know.

---

### Post by f00b on 2009-03-11
Is this worthy of logging as a request (bug) ?

---

### Post by Neo_The_User on 2009-03-11
yes (the most uninformed answer possible)

---

