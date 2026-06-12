---
title: "Bizarre behaviour, mouse, keyboard etc."
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by Declan on 2005-04-16
Well, the laptop has gone completely insane.  I
It doesn't boot up at all some of the time.  
When it does boot, it gets to gdm but the mouse is already only partly in control of the cursor.  At times the cursor goes and does its own thing entirely.
The keyboard no longer responds promptly.
As things stand, the computer is not usable (which is a problem).

I haven't really seen many error messages, but maybe there is one about psmouse and bad data.

I've tried going into a terminal in another terminal session, and it works at 90% (though not perfectly).

I wouldn't mind having to re-install Hoary (I'm now running on a system upgraded to Hoary), but I need to back up some stuff first.
Which, of course, I can't do since neither moure nor keyboard are doing their jobs properly.

The action which I took the evening before this problem manifested itself was to install Adobe Acrobat 7 from some other repository.  I don' t know if this was the cause of the difficulty.

Essentially, there are two kinds of ways out of this:
(1) To solve the problem directly,
(2) To manage to make a backup onto disk, and then reinstal Hoary.

Anyone any ideas?

Thanks indeed,

Declan

---

### Post by nad on 2005-04-16
The direct problem I do not know. If you suspect acrobat (without prejudice) removing the software could make it worse. Anybody? Obviously something to consider.

Short of pulling the drive and physically installing it temporarily in another computer, how about accessing the laptop through a network connection? You should be able to ssh into it to perform any necessary configuration prior to doing an nfs mount from your desktop. Then it is simply a matter of copying over.

I had originally thought to suggest using cdrecord from the command line (it is quite simple notwithstanding your flakey keyboard), however (post dinner and reflection), it appears to be broken. Apparently nautilus handles the translation to the writer (if it even uses cdrecord). Hand configuring cdrecord requires boot parameters and module additions. Post back with your thoughts. I'm be happy to help whatever your decision.

Dan M

---

### Post by Declan on 2005-04-17
Well thanks very much for the offer of help.  Actually, I've manage (by some class of miracle, I suppose) to backup some of the data.  I booted with the 386 kernel (I don't know if this made a difference or not), and managed to work almost normally for long enough to put together a gnome baker project with most of what I needed to save.  So that's done.  

All I have to retrieve now is the data from evolution and thunderbird (are they contained in ~/.thunderbird and ~/.evolution folders?  That would be convenient.

So there's progress there.
But I'm getting more concerned that the problem lies deeper than my installation.
The strange fact is that I can only boot once an hour, or thereabouts.
If I shutdown, the machine refuses to do a thing for about an hour.  
I imagine (in my ignorance) that the BIOS are telling the computer not to boot until a certain period has passed, or until the temperature is below a certain level.  But that's just a guess.

And, furthermore, the mouse and keyboard work funny both under a live-cd session which I tried with SimplyMepis 3.3 and the Hoary installation disk (with which I tried the early steps of a fresh installation).

I'm beginning to suspect that whatever the problem is will not be solved by freshly installing Hoary.

Hopefully someone can advise me otherwise.

It'd be sad to go to Toshiba and to have them tell me that my using Linux means that they won't help me sort out some hardware difficulty.

That's the latest.

Thanks for your kind response.

PS: the main error I got when trying the failsafe option on hoary was "psmouse.c : bad data from KBC - timeout bad parity".

Am I to despair?

Declan

---

### Post by nad on 2005-04-17
Laptop input devices take quite a beating. I regularly replace keyboards and pointer sub-assemblies.

The worst part about dealing with Toshiba will be dealing with a first level rep who will be stymied or recalcitrant to help because he won't be able to guide you through his diagnostic script. You will need to insist on bumping your problem to a higher level.

And, yes. Your data is all in your home directory. You do not have permission to write any place else!

Good luck,

Dan M

---

### Post by Declan on 2005-04-18
Right, I've successfully re-installed hoary.
At first I was delighted to see that everything was working fine.
I immediately installed 3 or 4 programs (nothing risky, fluxbox and stuff like that), rebooted, logged in and out.  Everything was just perfect.

But then, this morning the problems are back.  Perhaps worse.
Mostly the system starts, but not always.  But then, no matter what I do, the keyboard starts siezing up.  I've been forced to power down with the power button a few times.

I've been able to verify that the kernel is still complaining about psmouse.c: bad data from KBC - timeout bad parity.  

Questions: what might this mean?
Is it fair to assume that the fact that I got 2 hours of perfect response from the new install means that the hardware was not presenting any difficulty during this time?
But if it is not a hardware fault, then how come the problem persisted through a disk format and a reinstallation?

I really am not looking forward to going to Toshiba about this, especially if I have no clue what the problem is.  

Looking forward to your kind assistance,

Declan

---

### Post by nad on 2005-04-18
Regardless of Toshiba's broken hardware and/or firmware, this would be a tough call for their support department. After all it probably works fine in the other (more forgiving | hobbyist | firmware is written for it) operating system.

Presently work is under way in the kernel to handle your issue more gracefully. One such kernel patch is described at:

[http://www.gossamer-threads.com/lists/linux/kernel/514252?do=post_view_threaded](http://www.gossamer-threads.com/lists/linux/kernel/514252?do=post_view_threaded)

Regards,

Dan M

---

### Post by Declan on 2005-04-18
Wow, well done for digging that up.  I don't know what it means, but it looks good.

I'm tempted to think that it doesn't even depend on the operating system, inasmuch as even the pre-boot bios editing screen (where you get to change the boot sequence etc.) shows signs of suffering from the problem of locking keyboard.  

Should I conclude a hardware problem?
And if so, is there any possibilty that it may have been caused by some action of mine (I'd imagine not, unless I had dropped the computer, or caused it some physical damage).  


Declan

---

### Post by nad on 2005-04-18
Hardware/firmware? Is there a bios update for your machine?

You will have to search Toshiba's support to see if this is a known problem. If so, there should be no problem with an in warranty repair. Otherwise, it could be an uphill battle. I would explore the issue with Toshiba nonetheless.

Dan M

---

