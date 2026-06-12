---
title: "Newbie - Login to Ubuntu 9.04 problems"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by hklozzo on 2009-04-19
Hello to everyone,
Hope you can offer a solution to my problem.
I had previously tried earlier versions of Ubuntu from a Live CD and although i never seriously tried to use it alongside XP, i did enjoy trying it out. So when i saw that a new version (9.04) was just released, i thought i'd try it out again. So, me being over enthusiastic installed it as a dual-boot install alongside windows.
The install seemed to go fine, no error messages that i could see. But heres, the problem. I can't even login to Ubuntu at all after i boot-up to it.
I've tried everything that i can think of. Even booted to the Live CD version, checked the USER options in the admin menu, added a new user and set passwords, booted to the safe mode version ( that just doesn't help - only a menu with an option to boot normally!!).

So, i'm lost. I thought Ubuntu was all about being easy to use now but it is doing a pretty good job of not allowing me to even get through the front door.

I realise this would be simple to solve for most of you seasoned Ubuntu or Linux users but this MS XP user is stumped. Even XP allows you to get inside the system first of all and set passwords afterwards.

Solutions:
1. If one of you lovely people can advise a) how i can login-in, b) or how to avoid having to login at all?

2. If i can't get past this, how do i 'uninstall' Ubuntu?
   ( i beleive it has set-up a new partition ? But XP is not seeing it, so how do i get the space back again through XP?)

If anyone one could help me out, i would be grateful. I really would like to be able to keep Ubuntu as a dual boot option, so that i can spend the time learning it.

Thanks in advance for any help offered.

BR

---

### Post by labinnsw on 2009-04-19
Someone else might have a better solution but I have not looked at Jaunty yet.

What I am recommending is that you use the same ubuntu partition to install Intrepid instead. While installing you will be presented with a check box to login automatically.

Doing an upgrade to Jaunty should be simple enough and it should also retain the Intrepid settings.

Windows cannot as far as I know read linux partitions. The Windows installion CD will only see an unknown partition which it can format to FAT or NTFS or delete. *(If you really want to erase the ubuntu partition)*

If installing Intrepid works, then I think your other questions will be answered.

---

### Post by coffeecat on 2009-04-19
> **hklozzo said:**
> But heres, the problem. I can't even login to Ubuntu at all after i boot-up to it.

Please explain exactly what you mean. Do you get the graphical login screen? If you do, does it prompt you for your username and password? Does it throw up an error message?

I've installed Jaunty to four systems now: 2 laptops, 1 desktop and as a virtual machine in VirtualBox running in MacOS. Login is fine in all of them, so there's something specifically gone wrong in your installation.

> **hklozzo said:**
> I've tried everything that i can think of. Even booted to the Live CD version, checked the USER options in the admin menu, added a new user and set passwords, booted to the safe mode version ( that just doesn't help - only a menu with an option to boot normally!!).

A couple of words of explanation. If you boot to the live session and add a user, you've only added a user to the live session, not to your hard disc installation. If you boot in safe mode from the hard disc, you can change the password of your ordinary account with a command-line command - if it is the password that is the problem. But before we try that, let's see what the details of your login problem are.

---

### Post by hklozzo on 2009-04-19
Hi Coffeecat,

Ok, heres what i see:

1. Switch on my pc - a dos screen asking me to choose between Windows XP or Ubuntu.
2. Choose Ubuntu - it shows a splash screen with loading graphic
3. Comes to a black screen with box in centre asking for password. There is an options menu in lower left with options to reboot/change user etc.
4. Whatever i type in the username box, it then asks for a password.
5. Error msg is wrong username/password.
6. I've tried leaving it blank / entering new login details / u:ubuntu p:ubuntu / u:root p:root etc..

Nothing seems to let me get past this screen.

Note: When i was installing, i was never given any set-up options to choose a username. The installation just went ahead and installed itself. Is this what is causing the problem?

I agree regarding the user settings with a Live CD session. I knew it would be the case, i was just trying everything i could think of at the time.

I know nothing about Linux o/s's except theres a lot of strange commands entered through a terminal ( reminds me of the long ago days of DOS commands).

If you got a simple solution for me to get past this, i'd be very grateful.

Thanks for the replies so far!

br

---

### Post by labinnsw on 2009-04-19
Reboot your system.
When you see the word GRUB, press the Esc key.
At the prompt type:

> passwd <username>

Follow the prompts, then reboot.

> reboot

---

### Post by coffeecat on 2009-04-19
> **hklozzo said:**
> Note: When i was installing, i was never given any set-up options to choose a username. The installation just went ahead and installed itself. Is this what is causing the problem?

Were you using the live CD? If, so there is no way that I know of that you could have avoided this screen:

[IMG]http://news.softpedia.com/images/extra/LINUX/large/ubuntu804installationguide-large_008.png[/IMG]

That is from the 8.04 installer, but the 9.04 installer at this stage is the same. The only way I know of to avoid selecting a username and password is to use the alternate CD and do an OEM installation. But that's a different matter.

I could tell you how to change the password in safe mode, but if you don't know what your username is, then that won't help I'm afraid.

If you are absolutely, 110% sure that you did not see that screen with the live CD installer, then I suggest you try installing again. If you do get that page, please make sure to make a note of the username and password you choose. If you don't get that page, then you've uncovered a very obscure bug which needs to be reported. If you have, please post back.

Good luck.

---

### Post by coffeecat on 2009-04-19
> **labinnsw said:**
> Reboot your system.
When you see the word GRUB, press the Esc key.
At the prompt type:

> passwd <username>Follow the prompts, then reboot.

You forgot to say: boot into safe mode.

But the OP doesn't seem to know their username, if I am reading the posts correctly, so that is not going to work.

---

### Post by hklozzo on 2009-04-19
Hi all,

Thank you very much for the replies. Coffeecat, i can confirm that i absolutely did not see that screen ( it would seem pretty clear if i had spotted that ). Trouble is, i can't quite remember the method i used for installing. I beleive it was by inserting the CD whilst XP was still running and an option screen appeared with the choice to install Ubuntu as an application alongside XP.
I don't think that i rebooted to the CD and installed from there.

Anyway, long story short. I have now downloaded and installed v8.10. It seems to have installed OK and i DID see the initial screen you showed above. It has installed and i have been able to log-in OK with my chosen log-in details.

Infact, i'm posting this whilst running ff on Ubuntu.

I want to thank you all for the replies but i think i'll keep things this way for a while until i learn Ubuntu some more.

Thanks again.
That'll teach me to mess around with beta versions!

---

### Post by coffeecat on 2009-04-19
> **hklozzo said:**
> Trouble is, i can't quite remember the method i used for installing. I beleive it was by inserting the CD whilst XP was still running and an option screen appeared with the choice to install Ubuntu as an application alongside XP.

That might have been [Wubi]("https://help.ubuntu.com/community/Wubi"). In which case you should have seen:

[IMG]https://help.ubuntu.com/community/Wubi?action=AttachFile&do=get&target=Wubi3.png[/IMG]

:wink:

Whatever - I'm glad it's sorted. Very best wishes for your Ubuntu-ing.

By the way, the terminal might appear to be forbidding, but it's OK once you get used to it. And, in fact, for very many things there are GUI ways. Some people get away with not using the terminal at all, or not very often. Just be aware that there are a lot of terminal aficionados on this forum, who often post terminal code when a couple of mouse clicks might do the trick. Ho hum.

But such is life. :p

**Edit:** sorry, just remembered. If it was Wubi and the Jaunty Beta, I believe there was a significant bug with the Jaunty Wubi a week or so ago. Can't remember the details though. And if it was Wubi and you haven't uninstalled the Wubi-ised Ubuntu, there'll be a C:\ubuntu folder in Windows.

---

### Post by rajeeja on 2009-07-13
Problem loging on to the internet (being admin) after installing Eucalyptus, now my host is localname.localdomain instead of my system name. 

Any solutions highly appreciated.

---

### Post by rajeeja on 2009-07-14
Fixed with a fresh install !

---

