---
title: "cant start partitioner HELP!!"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by markcaetano@gmail.com on 2005-12-09
hi!!

i cant install my ubuntu 5.10 pc version (x86)
everything goes perfect un til it gets up to the partition editor it will get up to 52% quickly but then it wil stop there i tried it several times and left it for 3 hours but still stayed in the same place

specs are as follows

IBM aptiva(1999-2000 ish)
AMD K6-2 450 Mhz
SIS 530 motherboard 66 Mhz
Quantum fireball hdd 10.53 GB
64 mb ram (100Mhz sdram)
windows 98 (still installed)

PLEASE HELP ME A.S.A.P!

---

### Post by az on 2005-12-09
[QUOTE=markcaetano@gmail.com]hi!!

i cant install my ubuntu 5.10 pc version (x86)
everything goes perfect un til it gets up to the partition editor it will get up to 52% quickly but then it wil stop there i tried it several times and left it for 3 hours but still stayed in the same place

specs are as follows

IBM aptiva(1999-2000 ish)
AMD K6-2 450 Mhz
SIS 530 motherboard 66 Mhz
Quantum fireball hdd 10.53 GB
64 mb ram (100Mhz sdram)
windows 98 (still installed)

PLEASE HELP ME A.S.A.P![/QUOTE]

If you hit CTRL-ALT-F3, you get to see the error display.  Anything intersting there?  If your keyboard is frozen, you can reboot and switch to that screen before it freezes again.

---

### Post by markcaetano@gmail.com on 2005-12-09
can u say that again ,but explain it better i m new 2 ubuntu

---

### Post by dcast on 2005-12-09
Is it a bad cd? I had that happen once where everytime i tried it froze up in the same spot.

---

### Post by markcaetano@gmail.com on 2005-12-09
i tried another cd and it still didnt work 
but many other people are having the same problem
it freezes at 52% all the time
i dont want to uninstall 98 cos im going to install GRUB later

---

### Post by JoshHendo on 2005-12-09
> 
IBM aptiva(1999-2000 ish)


I have tried to install ubuntu on one of these computers and it didn't work. I tried everything. Also, I am sure it wasn't the CS as it was from shipit. Sorry about this :(

-Josh

---

### Post by markcaetano@gmail.com on 2005-12-09
thanx josh 
but would it help if i formatted the hdd 
(cos i backed all my stuff up to a dvd)
and started with a fresh install without 98 on there

---

### Post by az on 2005-12-09
[QUOTE=markcaetano@gmail.com]can u say that again ,but explain it better i m new 2 ubuntu[/QUOTE]
Just before it freezes on you, press CTRL, ALT and the F3 key together.   You will jump to a different display and error messages will show up.  Can you post them (or a reasonable facimile) here?

---

### Post by markcaetano@gmail.com on 2005-12-09
hi azz

i dont have a fax machine as i am only 13
and dont want to send an international letter

if u have one, can u send me your email address

mine is 
[email]markcaetano@gmail.com[/email]

---

### Post by az on 2005-12-10
No, I meant the opposite - Since it is written on the screen, you can just post what you remember to be the last few lines and we'll try to figure it out here.

By post, I mean post a message on the forum.


Don't give up!



(I wish I was only 13 :) )

---

### Post by SickTwist on 2005-12-10
Mark,

You may need to experiment with some special boot options that will keep the computer from freezing.

When the Ubuntu install CD starts there is a screen with the Ubuntu logo. When you see this screen you type the word linux followed by any special parameters that you wish to try. You can press F1, F2, F3, etc. to see some of these options. You can combine as many options as you'd like and hopefully you'll find a combination that allows the install to continue. Here is an example you might wish to try first:

linux acpi=off noapic nolapic pci=noacpi

Another thing crossed my mind: You might not have enough RAM for Ubuntu. 64 MB is on the short side and part of that amount might be used for your video card if it is onboard (part of the motherboard). That means that you might have 60 MB or less memory available for the system. This is not enough for the install to run (I think the server install requires 64 MB). You may want to consider upgrading the memory if that is possible or trying the install on another machine. Best of luck!

---

### Post by markcaetano@gmail.com on 2005-12-12
dear sicktwist

it dosent freeze as in completely lock up
and i cant get adittional ram for it if i can can u point me in the right direction

---

### Post by markcaetano@gmail.com on 2005-12-12
Another thing crossed my mind: You might not have enough RAM for Ubuntu. 64 MB is on the short side and part of that amount might be used for your video card if it is onboard (part of the motherboard). That means that you might have 60 MB or less memory available for the system. This is not enough for the install to run

---

### Post by SickTwist on 2005-12-12
Turn off the computer, open up the computer case and see if you have any empty RAM slots. If so and you feel comfortable about installing memory yourself, you could check local computer shops to see how much it would cost to buy a stick of RAM. It may be cheaper if you buy it used from a small computer repair shop. If you want to buy it new, check out [NewEgg.com]("http://www.newegg.com/")--I buy a lot from NewEgg and have never been let down. I found [this]("http://www.newegg.com/Product/Product.asp?Item=N82E16820146300") 128 MB stick which would work well for you and it's not too expensive.

 If you'd rather not pay for it, keep an eye open for old computers that people are throwing/giving away. At least another 64 MB stick of RAM would greatly improve performance on that machine. However, memory can't do miracles so it still might be a good idea to run Ubuntu with a lightweight desktop (Blackbox, Fluxbox, XFCE, IceWM, fvwm, fvwm95, etc.) instead of GNOME or KDE.

By the way, there is always the possibility that Ubuntu will not install on that machine for some odd reason (although perhaps [another]("http://www.distrowatch.com") Linux distro will) so keep that in mind if you are thinking of investing money in new hardware. On the other hand, even if you keep Windows 98 on there it could still benefit from extra memory.

---

### Post by markcaetano@gmail.com on 2006-01-31
i have gained some knowlege about the beautiful thing that is linux
and set up a dual-boot with win98

could i ask a moderator to put this thread up as a sticky for a week in the beginners section
as a reference for the less ubuntu literate cos it is free but still the best damn
OS i have ever used :cry:  BETTER THAN OSX:cry: 

please put this up as a sticky even for 5 days in the beginner section

---

### Post by RavenOfOdin on 2006-01-31
Try BootIt NG (link in my signature) -  For me, it successfully re-sized a drive which the installer couldn't sense any free space on, and I went from there.

So it could help you with this problem. You never know.

---

### Post by dada66 on 2006-01-31
Hi,

same problem here : the installation freeze during "Starting up the partitioner" at 52%.

This is an old PC, with win98, 64MB RAM, 2 HDD with some free place.

What happens :
a first progress bar concerning the partitioner appear in the selected language "demarrage de l'outil de partitionement", it goes up to 100%. Then a black screen, a grey screen, and then a new progress bar in english "Starting up the partitioner", that always stop at 52%.

With Alt+F3 I can read these infos that appear before the last progression bar:


File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
No matching physical volumes found
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
No volumes groups found
Reading all physical volumes. This may take a while...


Does it look like a RAM problem ?
I've seen another post of someone blocked at 52% here [http://ubuntuforums.org/archive/index.php/t-91172.html](http://ubuntuforums.org/archive/index.php/t-91172.html)

---

### Post by markcaetano@gmail.com on 2006-02-10
no is not the ram ive since changed it and jacked it up to 96 mb

all the lines about da media descriptors
same lines with me

---

