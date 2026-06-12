---
title: "Can I do a fresh reinstall of 8.10 ..."
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by RVA Dennis on 2009-02-18
I have botched things rather badly in adding WINE, DOSBox, QEMU, etc and also drivers for ATI so I want to start over from scratch. I have partitioned my HD already so are the any special steps I should take to reinstall? (Roughly 50/50).

If not I can reinstall WinXP and then do an installation from the Ubuntu disk I recieved from Canonical, a real pain but I've reinstalled WinXP several times and am comfortable with that if need be.

Also If I do this can I change to boot order to WinXP as the primary until I get everything right and then step and boot into Ubuntu as the primary?

Sorry to sound so confused and uncertain but I am at this stage.

TIA Dennis

---

### Post by InspiredIndividual on 2009-02-18
What's your partitioning scheme?

---

### Post by RVA Dennis on 2009-02-18
Scheme is:

bfts 54
ext3 19
swap  1

---

### Post by howefield on 2009-02-18
> **RVA Dennis said:**
> ...I have partitioned my HD already so are the any special steps I should take to reinstall? (Roughly 50/50).

If not I can reinstall WinXP and then do an installation from the Ubuntu disk I recieved from Canonical, a real pain but I've reinstalled WinXP several times and am comfortable with that if need be.

Also If I do this can I change to boot order to WinXP as the primary until I get everything right and then step and boot into Ubuntu as the primary?

Both  options are pretty easy, to reinstall Ubuntu, just use manual partitioning during the install and tell the program to use the relevant partions and mark them for formatting.

For your second option, once you have windows and Ubuntu installed, download startupmanager from Synaptic Package Manager and use it to tell the system to make Windows the default boot.

---

### Post by RVA Dennis on 2009-02-18
Thanks very much howefield, I'' use manual paritioining as you suggested and then Synaptic as well.

Reall appreciate all the help and encouragment I've gotten for these forums!

Priceless.

---

### Post by howefield on 2009-02-18
No problem RVA Dennis, remember that a reformat is destructive, so back up anything that you need to keep. You most likely would do that, but just in case ;-)

---

### Post by RVA Dennis on 2009-02-18
I generally back up on the fly daily in WinXP - learned the hard way about that :( but in the case of Ubuntu I'm not backing up anything as I'd like to start clean slate even though the updating process is tedious but it is a good way to learn.

Cheers!

---

### Post by RVA Dennis on 2009-02-18
Haven't reinstallled yet but the boot change worked slick as oil. No problem doing it, thanks very much howefield.

---

### Post by RVA Dennis on 2009-02-19
Well I twice attempted to reinstall into the existing partition but got a message to the effect root was required. On the second attempt I went to install from the new temporary desktop and couldn't do more than further reduce my existing windows partition. 

What am I doing wrong here? I'd rather not reinstall XP and then Ubuntu as that would be rather time consuming and tedious but if I must then I will.

Any thoughts?

---

### Post by InspiredIndividual on 2009-02-19
What exactly have you done so far? I suppose you shut down your operating system and put the LiveCD in. Did you get to the LiveCD menu (options for example 'try without changes to your computer', 'memtest', 'install')? At what point did you get a message you needed to become root?

EDIT: Do I understand you correctly that with 'install from temporary desktop' you mean you booted the LiveCD (choosing 'try Ubuntu without changes to your computer') and clicked the 'Install' icon on the Desktop? Then, as you state you could make the Windows partition smaller, I suppose you chose 'Manual' for partitioning and got a window with different partitions? At that point, it should be possible to click the non-Windows partitions and remove them with 'Edit/remove partition' or something like that. After you've removed them, you can add the required partitions in the created free space. I hope this helps to narrow down where you get stuck...

---

### Post by RVA Dennis on 2009-02-20
Sorry to be so slow in responding Intrepid BUT ... the issue has been resolved, thanks to Microsoft. I stupidly followed their knowledge base instructions which of course failed to mention changing the MBR removing GRUB before attempting to delete a partition ... the rest is history.

In the end I was forced to do a fresh install of WinXP - four+ hours of hellish aggravation and another 90 or so minutes this morning to essentially be in position to get on with my life.

In any case I will be reinstalling Ubuntu 8.10 this weekend having learned several lessons from my first experience. 

Thanks for helping.

---

