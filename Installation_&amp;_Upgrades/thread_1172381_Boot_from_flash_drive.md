---
title: "Boot from flash drive"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by beacon on 2009-05-28
This is my first post, and I hope I haven't done the wrong thing by creating a new thread. There are a number of posts on related topics, but I haven't seen one that exactly fits my own problem.  I have installed Ubuntu 9.04 on my hard drive, and there has been no problem. Following the instructions in the January issue of Linux Format (admittedly they are discussing 8.10), I have tried to create a bootable flash drive so that I can have 'linux in my pocket', as they put it.   The difficulty is that I cannot get the flash drive to boot. My booting sequence in the bios is given as (1) removable disk); (2) CD/DVD and (3) Hard drive.No matter what I do, the first never works. If I put in a DVD, the computer will boot from that, and of course, from the hard drive as well. But I cannot start with the flash drive.  I have tried with puppy and minime as well,with no luck. Am I overlooking something quite simple?

---

### Post by miliamber on 2009-05-28
you can get info on making bootable thumb drives at pendrivelinux.com.

---

### Post by jimbo99 on 2009-05-28
Your bios needs to provide you with the option to boot from a USB device, such as a USB hard drive.  If not, then you won't be able to boot from the flash drive.  Check for a bios upgrade from your motherboard manufacturer for your exact model and revision of the motherboard.

Is the flash plugged in before you go into bios to check the boot options?

Hope that helps.

I just did a test install onto a flash drive and noticed that my boot device listing didn't give me the option of booting from USB.  So, with the device plugged in, I rebooted the computer, went into BIOS, then went into the section that covers determining which HDD is to be used as the boot drive (in the case you have multiple HDD drives), and saw the flash drive listed there.  I then moved it up in priority to become the first boot HDD.  After that I went to ensure that USB support was turned on (just USB support) and also enabled legacy USB support (whether this was critical or not I don't know).

I'm now using it to post this comment.

P.S.  I just confirmed that I needed to have USB Legacy Support.  I also noted that when I turned USB Legacy support off and rebooted, found that I needed it for it to boot off the flash drive, then went back to add it again, I found the USB device needed to be selected as the main HDD boot device again.  I suspect that you'd have the same issue if you just pulled the flash and rebooted and then reinserted it later and rebooted.

---

### Post by jimbo99 on 2009-05-28
I had a few questions myself come up regarding this.  Here they are:

1)  It appears that the program to create the bootable flash drive wants the device formatted in FAT32.  I can only wonder why.

2)  It appears that the program to create the bootable flash drive wants to set aside space for documents.  Wierd, just make a partition the way it normally is done.

3)  It appears that no matter how much space you set aside it's not the same amount that you set aside when you created the bootable flash drive.  For instance, I told the program that creates the bootable flash drive to set aside 8 gb out of 16 for documents, etc.  When I look it states that I have 1.4 gb free.  That's about 6.5 gb shy of what I stated. When I look at the part that holds the OS files it shows that there is a huge amount of space available..

Anyone have thoughts on these points?

---

### Post by jimbo99 on 2009-05-29
I did more testing on the flash drive component of Ubuntu.

I had a 2 gig flash drive. I initially attempted to create a bootable flash on that.  It worked, but there wasn't enough room to do any work.  I'd attempt to watch youtube.com and it would stop. After checking the amount of free space I decided to take a trip to the store and pick up a 16gig flash drive.

I then did the install on it.  I found a similar problem where I was informed I had only a small amount of free space where my documents, etc would be persistently stored.

This I took to be wrong so  I ran the USB Flash drive creator again and this time told it to increase the amount of space set a side for persistent documents to 8 gigs.  Then after rebooting I noticed that it wasn't saving my settings.

I took this to be wrong also.  I ran the USB flash drive creator and decided to leave it at the default settings.  I booted with it, installed firefox, existed normally.  Then checked to see if it had maintained my settings between sessions.  It did.  Firefox was there.

Not totally convinced I booted back to Linux on the HDD, I reran the USB flash drive creator and chose to use the maximum allowed space for persistent files.  I then rebooted, installed firefox and rebooted again.

Firefox was missing as was any customization I'd done.

I then did it again but left the usb flash creator options at the default and tried again.

I  then installed firefox and did a bit of customization.  When I rebooted into it firefox was there and so were all my customized settings.

It appears that the USB flash disk creator is flawed and that you are stuck creating one where the amount of space for persistent changes is so small as to be unusable.

Anyone have any thoughts?

---

### Post by beacon on 2009-05-29
Thanks for the helpful replies. I am writing now so I am not thought to be unappreciative, but I probably need more time to see if I can solve the problem. I thought I had done, but then things went topsy again, and I am re-reading the posts and trying to start again from scratch.

---

### Post by beacon on 2009-05-30
I think I am getting there. I followed the steps given in Linux Format magazine and seem to have got the flash drive to work. I booted from it, but now another problem has arisen. According to the magazine instructions, there will be a question about language, then ubuntu will appear, ready for customisation. However, after I tick the language, I get the start up page for ubuntu live disk, with options to try without changing anything on the hard drive, or install, etc. Once again, is it possible I have overlooked something simple?   I am, by the way, keeping in mind the suggestion about using pendrive linux, which I tried once before without any luck.

---

### Post by jimbo99 on 2009-05-31
Did you not try the built in tool that creates a usb flash drive for you?  The one installed when you installed Ubuntu?

That tool does work, though I think those that developed it are a bit confused.  It's a flash for on the go, meaning you would plug it into multiple computers over a given period of time.

I expect that these guys would be putting a great bit of effort in cleaning this up as it is a tool that demonstrates Linux to a greater number of people.  In other words, I can pull a flash drive out of my pocket, reboot, and demonstrate.  That's much improved over carrying CDs around.

If it wasn't for the unfortunate bug in creating the persistent file system things would be just fantastic with it.  As it stands now, with the bug in that regard it becomes nothing more than a for show failure, as you can show it but it fails at the ultimate purpose--to give you a portal linux with your configuration without the need for a CD/DVD.

OH, and BTW, what magazine are you talking about.  Can you link it so others, and myself, can review what you are talking about?

---

### Post by ardi28 on 2009-05-31
i didn't know it can be boot from flash drive, thats amazing.....
i'll try it...[:p:p:p:p]("http://webvaganza.com")

---

### Post by beacon on 2009-05-31
Thanks once again. I have been dealing all along with the 'create flash drive' tool, and it is that that has been causing all the trouble.I had assumed it would do what you say it won't do: that is, 'put Ubuntu in my pocket'. (I'm not sure what the unfuortunate bug is; tha main thing is that it seems not to create a usable flash drive.  Sorry, the magazine article was mentioned in my first post: Linux Format. January of this year.

---

### Post by thongkh on 2009-06-04
this is how i manage to get my usb presistant ubuntu 9.04 work after 'usb startup creator disk', i put the casper -rw file from pendrivelinux into usb root directory, now the 'live usb' able to save some setting, but unfortunately, it cant manage to update the system with update manager, it will come out with error saying /dev/.. something.. cant remember well.
 
need help about this problem, is it really cant update the 'live usb'? or there is something i need to config before that can happen.
 
please advice, thankz.

---

### Post by badbot on 2009-08-25
> **thongkh said:**
> this is how i manage to get my usb presistant ubuntu 9.04 work after 'usb startup creator disk', i put the casper -rw file from pendrivelinux into usb root directory, now the 'live usb' able to save some setting, but unfortunately, it cant manage to update the system with update manager, it will come out with error saying /dev/.. something.. cant remember well.
 
need help about this problem, is it really cant update the 'live usb'? or there is something i need to config before that can happen.
 
please advice, thankz.
 
"LIVE ubuntu" is not updateable.
your casper file will hold 1gb of data and/or changes.
[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)
this link has bigger casper files you can download.
 
what I did was disconnect all hard drives, load the CD and plug in my 8GB usb stick and ran install to 'disk' into the usb for a full ubuntu on a stick. I am running updates on it now.
 
IF you can choose the boot order and pick a usb with a full install you may well be able to do what you want to, windoz for the family and linux for you.

---

### Post by beacon on 2009-09-24
You can tell from my first post how long I have been trying to solve this problem. I have followed the article in Linux Format Magazine and used other methods and tutorials, and I still get no joy. Using the 'create' tool on Ubuntu I seem to be able to get Ubuntu on a flash drive. However, (again referring to Linux Format magazine), after rebooting you will be asked to choose a language, then you will be logged in as the live session user. In fact, what I get after selecting the language is the usual beginning, asking if I want to use Ubuntu without affecting the computer or want to install it. I am not logged in as a user. 

Any help will be gratefully accepted.

---

### Post by WolfRage on 2009-09-24
To get to your boot options with out reconfiuguring them each time, you should be able to press the "Esc" or escape key multiple times during your BIOS boot message. Then a blue screen should pop up which will allow you to choose which device you would like to boot from. However if a device is not on that list then it may be disabled via your BIOS or your motherboard may not support it.

---

### Post by beacon on 2009-09-24
Thanks Wolfrage. I have tried, but no luck yet. When I press esc I get 'installer boot menu, with the options to install, check cd for defects, test memory, advanced options, or help. 

I then checked the bios and found the flashdisk listed under HDD. I am sure that I ought to be able to get this to work, as I (finally) managed to boot  'Puppy' from a flashdisk. I wonder what the difference can be.

---

### Post by sukatto on 2009-09-24
I have finally (after many different attempts and methods) installed Ubuntu 9.04 on my 8GB SanDisk flash drive. I unplugged the hard drive from my computer and then used the install disk and chose use the entire disk and that seemed to work fine. It seems to be running a little slower than I anticipated but that may just be the computer. However, I am unable to access my onboard ethernet card. Any suggestions?

---

### Post by sukatto on 2009-09-24
I figured it out sorry. I put in an additional NIC, but it may have been solved by the reboot. Not quite sure, but it works!

---

### Post by WolfRage on 2009-09-24
If you want it to run faster you are going to need a lighter weight GUI. Try out Fluxbox or even XFCE.

---

