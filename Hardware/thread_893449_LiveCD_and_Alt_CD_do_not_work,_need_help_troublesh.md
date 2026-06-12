---
title: "LiveCD and Alt CD do not work, need help troubleshooting"
date: 2008-08-18
forum: Hardware
---

### Post by _radditz_ on 2008-08-18
Hi,

I have a packard bell F5280 spec:

proc: 2.8GHz Celeron
mem: 512MB DDR
GPU: SIS M661FX

I have checked and other users have successfully installed ubuntu on this laptop model see [here ]("http://ubuntuforums.org/showthread.php?t=113916")where another user is having sound problems.

I downloaded the live cd and when i try to start it, it freezes. It always happens at CUPSD see pic. I have waited 45 mins before switching the laptop off. The same happened when i selected OEM install.

[IMG]http://i302.photobucket.com/albums/nn100/_radditz_/SP_A0051.jpg[/IMG]

I posted this problem here and i was recommended to try the alt cd. I did that and again the install freezes for the following reason:

[IMG]http://i302.photobucket.com/albums/nn100/_radditz_/SP_A0053.jpg[/IMG] 

This is using the 7.04 liveCD and 8.04 alt cd. I dont know whats going wrong. I am hoping someone can really help as last time i only got 1 reply to this problem telling me to use the alt cd. I have heard so many good things about this community so that was a bit dissapointing!

Looking forward to solving this problem and converting a windows to a linux user!

Thanks!!

---

### Post by Sef on 2008-08-18
1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

3) Have you checked the cds to make sure they are ok?  Go down to 'Check disk for defects' instead of booting up or installing.

---

### Post by _radditz_ on 2008-08-19
checked both discs and they are ok. Did memtest and it found nothing either.

Any other ideas?

---

### Post by _radditz_ on 2008-08-20
bump

---

### Post by _radditz_ on 2008-08-21
bump

---

### Post by _radditz_ on 2008-08-22
bump

---

### Post by prshah on 2008-08-22
> **_radditz_ said:**
> 
I downloaded the live cd and when i try to start it, it freezes. It always happens at CUPSD see pic.

Does it actually freeze? Try the live CD once again, and when it reaches the CUPS line and there is no activity for a couple of mins, press ctrl+Alt+F1; do you see a login prompt?

---

### Post by _radditz_ on 2008-08-26
> **prshah said:**
> Does it actually freeze? Try the live CD once again, and when it reaches the CUPS line and there is no activity for a couple of mins, press ctrl+Alt+F1; do you see a login prompt?

Ok, I tried again and after 15 mins of waiting for CUPSD to load i pressed ctrl+alt+F1 and got the following message.

What should i do now?

[IMG]http://i302.photobucket.com/albums/nn100/_radditz_/SP_A0054.jpg[/IMG]

---

### Post by prshah on 2008-08-26
> **_radditz_ said:**
> 
What should i do now?


Give the command ```
startx
``` and post back error messages, if any. (There should be; to the effect "screens not found"/"no usable screens")

---

### Post by _radditz_ on 2008-08-26
thanks for the quick reply :). What should i do assuming i get the screen not found error message?

Saves me coming back to ask the question in 2 mins time.

---

### Post by prshah on 2008-08-26
> **_radditz_ said:**
> thanks for the quick reply :). What should i do assuming i get the screen not found error message?
Saves me coming back to ask the question in 2 mins time.

Sorry about that, I left after giving you a reply, and missed this message.

Did "startx" work?

---

### Post by _radditz_ on 2008-08-27
IT DID!!!

I managed to get into the desktop and doubled clicked install however the installation has frozen at 91% where it says "Loading module 'aec62xx' for 'IDE chipset support'".

What do i do now please? Its been like that for over 30 mins:confused:

edit: had to quit and shutdown in the end.

Can someone please tell me how to finish the reaming 9% of the installation please?

thanks

---

### Post by _radditz_ on 2008-08-28
bump

---

### Post by prshah on 2008-08-28
> **_radditz_ said:**
> 
Can someone please tell me how to finish the reaming 9% of the installation please?

[This post]("http://forums.parallels.com/showpost.php?p=54435&postcount=13") looks helpful, though they are talking about installing ubuntu in a virtual machine; take a look at the procedure, it may be helpful to you.

---

### Post by _radditz_ on 2008-08-28
I dont understand how I get to the rescue screen? Is a celeron a 386 or 686?

---

### Post by _radditz_ on 2008-08-28
i just downloaded xubuntu 8.04.1 in the hopes the up to date kernel would sort my problems out.

When i select start or install xubuntu the system hangs at cupsd again BUT when i press ctrl+alt+f1 all its says on screen is "Loading, please wait...".

I cannot enter "startx" to get to the desktop.](*,)]

---

### Post by _radditz_ on 2008-08-28
I managed to get to the 8.04.1 desktop by putting an "x" beside the first 3 options when you press F6. The no acpi etc etc.

I started the installer and it actually finished without a problem hurrah! BUT now when booting into xubuntu the laptop freezes as the blue bar just stops.

I pressed ctrl+alt+f1 and it says:

"kinit: No resume image, doing normal boot..."

There is no further text and the laptop has been like that for 20 mins. What do i do now?

edit: I may have found a solution [here]("http://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/") but when i select the recovery option in grub, xubuntu loads up to the point where it says:

"*Loading manual drivers..." and stops. 

I dont know how to implement the above fix now. 

And another thing, i've come to the forum for help and apart from prshah absolutely no-one is helping me. WTF gives people???

---

### Post by prshah on 2008-08-28
> **_radditz_ said:**
> apart from prshah absolutely no-one is helping me. 

I don't really seem to be getting anything useful done either ;) perhaps people are taking the cue from that :D

Aahh that impassioned plea...

> **_radditz_ said:**
> I dont understand how I get to the rescue screen? Is a celeron a 386 or 686? 

Don't boot off the live CD, can you manage to boot off your (partially) installed system? In that case, choose recovery mode, and follow the instructions from the link I've given previously.

Celeron is a 386-compatible 686. ;) Choose 686.

---

### Post by _radditz_ on 2008-08-31
tried to get into the recovery mode but the boot freezes at the same bit i.e. "loading manual drivers".

I cannot implement the fix if i get stuck at this bit.

I managed to boot from the livecd by activating the first 3 options in the f6 menu. Is there a way i can do the same for my installed ubuntu?

my reckoning is, if those options allowed the lived to boot then it should do the same for my installed version too.

---

### Post by _radditz_ on 2008-09-02
bump

---

### Post by prshah on 2008-09-03
> **_radditz_ said:**
> 
I managed to boot from the livecd by activating the first 3 options in the f6 menu. Is there a way i can do the same for my installed ubuntu?


What are the "first three options in the F6 menu"?

---

### Post by _radditz_ on 2008-09-03
Acpi=off
noapic
nolapic

---

### Post by prshah on 2008-09-03
> **_radditz_ said:**
> I managed to get to the 8.04.1 desktop by putting an "x" beside the first 3 options when you press F6. 

I dont know how to implement the above fix now. 


> **_radditz_ said:**
> Acpi=off
noapic
nolapic

To implement these options in your installed system, keep tapping ESC while booting (but after BIOS check) to enter the GRUB menu.

From this menu, select the choice you usually use to boot. DON'T press enter. Instead, press "e" to edit the choice. Now, select the line that starts with "kernel...", and again press e(dit). Scroll to the end of the line, and add the above three options (note all in lower case). I give below an example;
> 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4bce0fa6-bf3b-43dc-bd3c-9aac9b0d4eed ro quiet splash [color=red]acpi=off noapic nolapic[/color]
initrd		/boot/initrd.img-2.6.24-19-generic
quiet


When done adding the options, press enter to save the line, then press "b" to boot.

If this works out, post back on how to make it permanent.

Please use the system for atleast 30 mins before you decide everything is OK. In my opinion, you do not need all three options; just "acpi=off" should be enough, but it will require experimentation to find out which of these options are suitable for you.

---

