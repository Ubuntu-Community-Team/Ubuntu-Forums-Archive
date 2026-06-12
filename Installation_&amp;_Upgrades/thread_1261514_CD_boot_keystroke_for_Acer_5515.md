---
title: "CD boot keystroke for Acer 5515"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by jeannacav on 2009-09-08
What keystroke do I use to turn on my ACER 5515 from the live CD?
I am a mac user and I refuse to turn this laptop on because it is set to install vista and a bunch of things that will be locked in place. (Or, so I understand)
I do NOT want to use vista for one moment and I have not been able to find the keystroke to change the bios or just boot from the cd drive. (On a mac I hold the C for a bit and the Boot starts from the CD drive.) I am sure this same thing is possible on the acer 5515.

I have been reading this forum all day and the advice always seems to start with the machine already on. 

Please anybody?

CD boot keystroke for acer 5515

thank you,

jeanna

---

### Post by presence1960 on 2009-09-08
a good place to start would be your documentation that came with the lappie. If you don't have it look it up on Acer's site by your model.

---

### Post by jeannacav on 2009-09-08
Thanks

That is where I started earlier today.
I just cannot find it.
The consequences for trying the wrong one are that the vista will self install and lock itself in disk recovery mode... forever.

I also emailed acer.
The reply was so bad I laughed.
They told me I had mistyped my (22 character) serial number, and asked me to resubmit it.
As though that should be a prerequesite for learning how to boot from a cd!

Anyway, I am still hoping someone who has one of these can use it to tell me how.

jeanna

---

### Post by presence1960 on 2009-09-08
> **jeannacav said:**
> Thanks

That is where I started earlier today.
I just cannot find it.
The consequences for trying the wrong one are that the vista will self install and lock itself in disk recovery mode... forever.

I also emailed acer.
The reply was so bad I laughed.
They told me I had mistyped my (22 character) serial number, and asked me to resubmit it.
As though that should be a prerequesite for learning how to boot from a cd!

Anyway, I am still hoping someone who has one of these can use it to tell me how.

jeanna

**it will not be locked in forever. you can delete those partitions after if you wish.** [U]For warranty purposes I would allow it to install and then make an image backup of the recovery partition so you can put it back & restore the factory image (Vista) if need be.
[/U] Then you can use gparted to delete those partitions- recovery & Vista.
Think about it before you hastily remove your Acer recovery partition before it is installed & backed up.

> also emailed acer.
The reply was so bad I laughed.
They told me I had mistyped my (22 character) serial number, and asked me to resubmit it.
As though that should be a prerequesite for learning how to boot from a cd!

That may be valid as different models may have different methods of choosing the boot order, BIOS, etc.

---

### Post by hansdown on 2009-09-08
Hi jeannacav.

Hold ESC while it starts up to get to the boot menu.

---

### Post by jeannacav on 2009-09-08
Well acer finally answered me.
But it doesn't work at all now.

I am supposed to push F2 to change the bios.
So I did.
Maybe there is something wrong with the cd.
It took over 6 hours to download so I am just hoping for the best, but with the bios changed to CD there is nothing short of installing leopard that I can use if this cd doesn't work.
I guess I should order one from the ubuntu store??

Good thing I have my other computers!
I do want this to work, though. I am looking forward to it , in fact.

I am not sure how to get it to start now. I'll check out other threads. I saw some where folks were getting a blank screen on their acers.

I guess I am having an adventure!

thanks,

jeanna

---

### Post by jeannacav on 2009-09-08
Thanks hansdown,

True the nature of microsoft this has completely ignored everything I did.

It has started vista.

oh darn!

I hope the ubuntu can wipe this clean!

Now, what should I do? I wasn't prepared for this. I do not want to learn any windows just to get rid of it. hmm. I guess I must learn a little. oh barf!

Well, it was not off is the reason I got no response. Maybe the esc plus on button closed it down? I held it for a while?

egads! I thought I would never have a microsoft machine again. I am traumatized!

====

OK 
So, does anybody know how I can just make it look at the cd so I can open ubuntu?

thanks,

jeanna

---

### Post by presence1960 on 2009-09-08
> **jeannacav said:**
> Thanks hansdown,

True the nature of microsoft this has completely ignored everything I did.

It has started vista.

oh darn!

I hope the ubuntu can wipe this clean!

Now, what should I do? I wasn't prepared for this. I do not want to learn any windows just to get rid of it. hmm. I guess I must learn a little. oh barf!

Well, it was not off is the reason I got no response. Maybe the esc plus on button closed it down? I held it for a while?

egads! I thought I would never have a microsoft machine again. I am traumatized!

====

OK 
So, does anybody know how I can just make it look at the cd so I can open ubuntu?

thanks,

jeanna
Most machines have a message when you boot press <key> to enter BIOS or Setup. mine is Delete. Sometimes it flashes by fast, if you need to hit the pause key and it will halt POST and you may see the message. it usually comes up first with the BIOS or ACER logo. once in choose to set CD first in boot order of your devices. Save to CMOs and continue booting.

Most machines have the CD drive as first boot by default. Are you sure you burned the Ubuntu iso as an image to CD, not a data CD? 

If that doesn't work you need to read your documentation and find out what key you press to get into BIOS or Setup.

---

### Post by presence1960 on 2009-09-08
> **jeannacav said:**
> Thanks hansdown,

True the nature of microsoft this has completely ignored everything I did.

It has started vista.

oh darn!

I hope the ubuntu can wipe this clean!



thanks,

jeanna

Your vista is preinstalled already, so you have a Vista partition and at minimum an Acer recovery partition. 

Don't fret you can remove those partitions when you install Ubuntu by choosing the use entire disk option, or removing those partitions with gparted and creating your own partition scheme, then when installing Ubuntu choose the Manual (advanced) option

---

### Post by jeannacav on 2009-09-08
Wow,

I am speechless.

I have managed to get the cd to open and read it using notepad. Happily (for now) the wireless is not connecting to my modem, so it is still in a private situation.

I don't want to use the wubi. There is an autorun. Is that the installer?
If it is can I do the partition changes now?

thank you,

jeanna

---

### Post by presence1960 on 2009-09-08
> **jeannacav said:**
> Wow,

I am speechless.

I have managed to get the cd to open and read it using notepad. Happily (for now) the wireless is not connecting to my modem, so it is still in a private situation.

I don't want to use the wubi. There is an autorun. Is that the installer?
If it is can I do the partition changes now?

thank you,

jeanna

you can not install Ubuntu on a dedicated partition by reading the CD. You must boot from the CD just as you would to install Windows from a windows install CD.

If you want to use wubi, which you said you do not ( I concur on that) you would have to open the CD from inside windows and execute the wubi file by double clicking it.

---

### Post by presence1960 on 2009-09-08
[https://help.ubuntu.com/9.04/switching/installing.html](https://help.ubuntu.com/9.04/switching/installing.html)

If I may suggest you do some reading from the above link so you can see what I am saying about installing Ubuntu and the question about whether you burned the iso as an image to CD instead of just burning a data Cd- there is a major difference. that may be why your Ubuntu CD is not booting.

---

### Post by jeannacav on 2009-09-08
Since it ignored my order to boot from the CD before I wonder if it would ignore me again?

It was clearly doing an execution of some plan because it checked the drives and lots of stuff which took a long time.

I guess I could shut it down and try to get it to boot from the cd again. Just in case it works this time.

I think this time I will wait for a reply. (:) )

thanks ,

jeanna

---

### Post by presence1960 on 2009-09-08
> **jeannacav said:**
> Since it ignored my order to boot from the CD before I wonder if it would ignore me again?

It was clearly doing an execution of some plan because it checked the drives and lots of stuff which took a long time.

I guess I could shut it down and try to get it to boot from the cd again. Just in case it works this time.

I think this time I will wait for a reply. (:) )

thanks ,

jeanna
I don't think it ignored you, I think it is a matter of the CD not being burned as an image. if the CD isn't a bootable image it will not boot from CD and move on to booting from the hard disk. it is a machine and will only do what it is told to do. if no bootable Cd image is in the CD drive it can't boot  from that CD.

---

### Post by presence1960 on 2009-09-08
here is a screen shot of what my bootable jaunty install image looks like. Compare your CD contents with this and report back

---

### Post by jeannacav on 2009-09-08
Yes,
It has 13 folders/files like yours

1 is the wubi installer.

4 appear to be text docs and the one called "ubuntu" is empty.

8 are file folders one of which is called install.

I downloaded the *.i386.iso yesterday and burned it with disk utilities which has never failed me.

jeanna

---

### Post by presence1960 on 2009-09-08
Ok looks good, but sometimes looks are deceiving. I know this is trying your patience. I want to go back to the beginning. After you downloaded your iso did you [MD5SUM ]("https://help.ubuntu.com/community/HowToMD5SUM")the iso? if even one character does not match exactly the iso is corrupted.

Like I said I know this is messed up , but since your burned image appears to be ok, it can only be 2 things: either the iso was corrupted or the CD drive is not set to boot first. 

Oh yeah did you burn to a CD-R or DVD-R at a slow speed (4x-8x is good)? For data CDs/DVDs high speeds are great but for bootable images and large files not so good.

---

### Post by jeannacav on 2009-09-08
> **presence1960 said:**
> Ok looks good, but sometimes looks are deceiving. I know this is trying your patience. I want to go back to the beginning. After you downloaded your iso did you [MD5SUM ]("https://help.ubuntu.com/community/HowToMD5SUM")the iso? if even one character does not match exactly the iso is corrupted.
No, I did not do that. (6 hours was about it for me!)

> Like I said I know this is messed up , but since your burned image appears to be ok, it can only be 2 things: either the iso was corrupted or the CD drive is not set to boot first. 
OK so since I guess the bios got changed it must be this, but I do have the cksum in one of those files which I could read on my mac.

I don't remember what to do. I guess it is on the download page. Can I still do it?

> Oh yeah did you burn to a CD-R or DVD-R at a slow speed (4x-8x is good)? 
Yes, 4x (my policy with everything)

I wonder if my bios change was overridden since I had never turned on the computer before? (It needed my acceptance of the license, you know.)

thank you,

jeanna

---

### Post by presence1960 on 2009-09-08
> **jeannacav said:**
> 

I wonder if my bios change was overridden since I had never turned on the computer before? (It needed my acceptance of the license, you know.)

thank you,

jeanna
 if it is that i would be surprised, but you never know with microsoft what deals they cut with vendors. I would go ahead and accept the license agreement because when I was looking on line at Acers site i saw you have a GUI program within Vista to set the order of booting in BIOS.

If it is the acceptance of the license agreement we were doing this all along  ](*,)](*,)](*,)

P.S. they probably want you to accept the license before you can use the machine since Vista is preinstalled.

---

### Post by jeannacav on 2009-09-08
Thanks so much presence,


Just one more thing...
I have been looking for the chechsum directions.
Could you point me to the page?

I got to it after the 6 hours but there must be a quicker way! :) 

I have many hours left to the evening, but it is getting late on the east coast and I want to say how I do appreciate your help.

thank you,

jeanna

---

### Post by presence1960 on 2009-09-08
> **jeannacav said:**
> Thanks so much presence,


Just one more thing...
I have been looking for the chechsum directions.
Could you point me to the page?

I got to it after the 6 hours but there must be a quicker way! :) 

I have many hours left to the evening, but it is getting late on the east coast and I want to say how I do appreciate your help.

thank you,

jeanna
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

here is the page for Ubuntu hashes: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

You are welcome. I was new to ubuntu once also.

---

### Post by jeannacav on 2009-09-09
I think I should end this with an explanation of how it all finished.
A good ending-- to a newubu beginning.

Before messing with the terminal of my mac just to checksum the disk, I returned to the bios of the acer.

F2 at the startup.

I looked carefully at the list and because I had been using the optical drive I saw its name there. It had a very long inscrutable name but I saw the letters opti in between some numbers.

That was not the thing I had moved to the top. What I had moved to the top was a CD-ROM drive (with usb connection!), which was all I could find earlier.

So, I moved the optical drive to the top of the list and restarted and... ta da! the installation began.

I redid the partitions etc, and after I used it for a while the wireless began to work! so I was even online. ooo cool.

Thanks everyone especially presence1960 for all the help.

This final explanation is because,I am hoping/assuming my experience will help other noob's.

jeanna

---

### Post by presence1960 on 2009-09-09
> **jeannacav said:**
> I think I should end this with an explanation of how it all finished.
A good ending-- to a newubu beginning.

Before messing with the terminal of my mac just to checksum the disk, I returned to the bios of the acer.

F2 at the startup.

I looked carefully at the list and because I had been using the optical drive I saw its name there. It had a very long inscrutable name but I saw the letters opti in between some numbers.

That was not the thing I had moved to the top. What I had moved to the top was a CD-ROM drive (with usb connection!), which was all I could find earlier.

So, I moved the optical drive to the top of the list and restarted and... ta da! the installation began.

I redid the partitions etc, and after I used it for a while the wireless began to work! so I was even online. ooo cool.

Thanks everyone especially presence1960 for all the help.

This final explanation is because,I am hoping/assuming my experience will help other noob's.

jeanna

Glad to hear that! Enjoy Ubuntu.

---

