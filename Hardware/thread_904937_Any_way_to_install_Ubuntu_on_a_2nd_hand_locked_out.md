---
title: "Any way to install Ubuntu on a 2nd hand locked out laptop?"
date: 2008-08-29
forum: Hardware
---

### Post by scalywag66 on 2008-08-29
Actually 3rd hand.

My friend gave me an IBM laptop not to long ago that came from his job at Motorola when they were giving some  workstation laptops away to employees to take home when they were upgrading their workstations throughout the Motorola campus.

He said he barely used it a few times and had somehow lost the login and password, which I guess made it easier for him to hand it down.  So I figured since I like to think I know how to move around computers, I'd take it off his hands.

I was wrong, as I never bypassed the login despite using various methods and cracks etc I had used before that did work on other machines I'd been ask to bypass login due to dumb admin mistakes.  So I'm wondering if I can install Ubuntu through DOS on an .iso image cd with the installation on it using the cd boot-up method, as you would with trying to reinstall Windows Professional by cd(which I dont have) in order to start fresh and not be on a server domain.

Possible?

---

### Post by Therion on 2008-08-29
Assuming the password is at the OS level, yes.  You should be able to use a bootable CD or DVD to reformat and reinstall.  If it's a BIOS level Password, though, all bets are off.

You can use an Ubuntu LiveCD or download and burn a bootable copy of an application GParteEd.  

GPartEd will ONLY allow you to format and partition though; a LiveCD will allow you to do that AND install Ubuntu.

---

### Post by scalywag66 on 2008-08-29
Excellent!!!

You know how usually the login pass for Administrator is

```
Login:Administrator
Password: 
```Well, what I think my friend did was make a dumb password he couldn't remember for Administrator login and more or less locked himself out.  Some cracks I have on disk that need to run on cd boot-up in order to fix, always get hung up on the boot-up and I just power the thing off.  I would like to get that laptop going with Ubuntu and give it to my girlfriend who wants one DESPERATLEY, just to go on MySpace & PerezHilton.com [IMG]http://www.systemwars.com/forums/images/smilies/sad.gif[/IMG]

Likewise, can't I also borrow a copy of Windows Professional from my brother or someone who I know has it on CD and install it using the same boot up method and the Windows Professional key that's under the laptop?

---

### Post by nicedude on 2008-08-29
Maybe your key on bottom will work but maybe not. Also you never said if the laptop has a bios password because if it does then that is another matter to remove although not impossible as you can try either removing all power and battery and then you would have to take the bottom off and find the system backup clock battery and try removing it, if that doesn't work then you can also short the contacts of the system clock battery for a few seconds and that can do the trick as well but both of those are a little advanced since they require taking it apart etc. but I have gotten rid of laptop cmos passwords in this way before. If however it is a Windows login password then whatever just wipe the whole darn drive with DBAN ( google dban its free and everyone should have a copy ) and start fresh by then installing Ubuntu or dual boot Ubuntu & XP.

---

### Post by Therion on 2008-08-29
> **scalywag66 said:**
> Excellent!!!

You know how usually the login pass for Administrator is

```
Login:Administrator
Password: 
```Well, what I think my friend did was make a dumb password he couldn't remember for Administrator login and more or less locked himself out.  

<snip>  

Likewise, can't I also borrow a copy of Windows Professional from my brother or someone who I know has it on CD and install it using the same boot up method and the Windows Professional key that's under the laptop?
Windows is licensed differently than Ubuntu is, and each XP license is good for an install on just one PC.  All I can say here is that with a legitimate WinXP install CD, and it's corresponding Product Key (the Key is "tied" to the individual CD), yes; you could then do a fresh install of Windows XP and resolve the Password problem.

Ubuntu, on the other hand, is free to copy and distribute - not too mention the superior OS - but do as you wish.

---

### Post by nicedude on 2008-08-29
He thinks he needs MS OS so his girlfriend can go to myspace and paris hiltons site and I dont believe that is the case at all. While I don't use Myspace I just went to paris hiltons site and everything there works fine for me, it even started playing her horrible music right away ( quite annoying ). So I think if anything all anyone needs is flash. Worst case scenario and a website requires IE to browse ( almost none do ) then I think I saw somewhere you could rig that up in Wine and fool the sites into thinking your using Windows anyway.

---

### Post by Therion on 2008-08-29
> **nicedude said:**
> He thinks he needs MS OS so his girlfriend can go to myspace and paris hiltons site and I dont believe that is the case at all. 
I think you misread his post.  He states he'd like to install Ubuntu and then give the  notebook, with Ubuntu on it, to his girlfriend so she will cave in and finally sex him up.

The WinXP question was just out of curiosity I believe.

---

### Post by scalywag66 on 2008-08-29
> **nicedude said:**
> He thinks he needs MS OS so his girlfriend can go to myspace and paris hiltons site and I dont believe that is the case at all. While I don't use Myspace I just went to paris hiltons site and everything there works fine for me, it even started playing her horrible music right away ( quite annoying ). So I think if anything all anyone needs is flash. Worst case scenario and a website requires IE to browse ( almost none do ) then I think I saw somewhere you could rig that up in Wine and fool the sites into thinking your using Windows anyway.

lol

No no no!!!

I meant my lady has been buggin me about getting her a laptop, or cries about how she can't afford one yet(which is her way of asking me for something without asking me directly), and since I wont let her use the laptop I have that is working properly(because she'll accept anything download wise), I'm thinking I can take this IBM and install Ubuntu  on it cause she likes how cool and flashy it is and give it to her so she could stop her crying.   

But since the Windows log in is locked out due to my dumb friend replacing Administrator password and not remembering it, everyone is locked out of Windows.  There is no password on the BIOS, so I am able to change the machine's boot-up process, and is why I am hoping I can install Ubuntu through the BIOS on a cd.   

I didnt't mean exactly MSDOS.  I just couldnt think of BIOS until I read your post.

I should be more clear, eh?  Sorry [IMG]http://www.systemwars.com/forums/images/smilies/icon_smile.gif[/IMG]

---

### Post by nicedude on 2008-08-29
Does this laptop have a CD drive? if so just get a copy of dban and a copy of Ubuntu burn them on CD's and first wipe the whole hard drive with dban and then install Ubuntu via the CD drive. Then she can click on any silly ad crap all day with no ill effects :-)

---

### Post by scalywag66 on 2008-08-29
> **nicedude said:**
> Does this laptop have a CD drive? if so just get a copy of dban and a copy of Ubuntu burn them on CD's and first wipe the whole hard drive with dban and then install Ubuntu via the CD drive. Then she can click on any silly ad crap all day with no ill effects :-)

Yes sir!!! As a matter of mact that's what I'm looking up right now and trying to get it done before I head out for a small bit. 

So then......all I'd have to do is burn the .iso to a disc, insert in the cd drive, reboot and change boot-up scheme from disk to cd, reboot and the installment should start?

I certainly hope so and that the installment doesn't get hung up

---

### Post by Loaded.len on 2008-08-29
Just a couple of points of interest.

A) Bypassing MS security (passwords) is dead against their EULA (like anyone cares) But it's quite simple to do with a live CD.

B) I think we've ruled out a BIOS level password, but all the same... IBM's BIOS security is, at least on some models, a joke (short out the PSWD jumper in the RAM compartment). However, HDD passwords on thinkpads in general are pure evil. You might as well forget it... you'll need to replace the motherboard and HDD at the same time to get passed it.

There's my two cents.

---

### Post by Therion on 2008-08-29
> **scalywag66 said:**
> So then......all I'd have to do is burn the .iso to a disc, insert in the cd drive, reboot and change boot-up scheme from disk to cd, reboot and the installment should start?
Yup.  That's how it's done.

> **scalywag66 said:**
> I certainly hope so and that the installment doesn't get hung up
Your biggest concern should be getting the wireless card connected.  Dollars to donuts, IF you have a problem, that's where it will be.  If you can wire it directly to your modem when you first start to install, that might be a good idea so you can get all the updates; which might better your chances for a smooth transition to a wire-LESS connection.


Best of luck!

---

### Post by jangari on 2008-08-29
> So then......all I'd have to do is burn the .iso to a disc, insert in the cd drive, reboot and change boot-up scheme from disk to cd, reboot and the installment should start?
That's all you need to do. In fact the BIOS may already be set up to boot from CD first, and if no bootable CD is found, to default to disk. Installation after that is easy, famously.

> Worst case scenario and a website requires IE to browse ( almost none do ) then I think I saw somewhere you could rig that up in Wine and fool the sites into thinking your using Windows anyway.
Actually, this is pretty common. Especially on the Microsoft pages, and some other places. I wouldn't be able to nav into some area unless I was using a particular browser (usually IE). There's a brilliant solution, though. If you use Firefox, get the add-on [user agent switcher]("http://chrispederick.com/work/user-agent-switcher/"). It'll let you change the signal your browser sends out that tells sites what browser and OS you're running. So you can pretend to be using WinXP and IE 7, or Safari on a Mac 10.5, whatever you like. It has come in handy many times for me.

---

