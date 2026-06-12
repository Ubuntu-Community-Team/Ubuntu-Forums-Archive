---
title: "Erratic touchpad and keyboard"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by groovomata on 2007-04-23
Hi All,
 I just installed feisty on my compaq V5000 laptop two days ago and since I've been plagued by very erratic synaptic touchpad and keyboard behaviour. The mouse seems to jump all over the place, sometimes locking onto things as if I've made a left click, sometimes it gets stuck and won't move, sometimes I can't select anything with it. I've installed GSynaptics and modified the xorg.conf file and made some adjustments - but to no avail. Additionally, my keyboard is acting up as well. Sometimes key input seems to get stuck and I will have a letterrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrr go across my screen (like that) or sometimes backspace - which is even worse because I can' stop it (I lost a whole email that way)!
I didn't have these problems with edgy. Has anyone had a similar problem? Would anyone know how to troubleshoot something like this?
Thanks in advance!
Erik.

---

### Post by solarix on 2007-04-23
> **groovomata said:**
> Hi All,
 I just installed feisty on my compaq V5000 laptop two days ago and since I've been plagued by very erratic synaptic touchpad and keyboard behaviour. The mouse seems to jump all over the place, sometimes locking onto things as if I've made a left click, sometimes it gets stuck and won't move, sometimes I can't select anything with it. I've installed GSynaptics and modified the xorg.conf file and made some adjustments - but to no avail. Additionally, my keyboard is acting up as well. Sometimes key input seems to get stuck and I will have a letterrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrr go across my screen (like that) or sometimes backspace - which is even worse because I can' stop it (I lost a whole email that way)!
I didn't have these problems with edgy. Has anyone had a similar problem? Would anyone know how to troubleshoot something like this?
Thanks in advance!
Erik.

I had a similar Problem on my IBM Thinkpad A 31 with Ubuntu Feisty Fawn. The Issue was also present with Dapper but not on Edgy, a workaround for me was to remove the IBM tpctl and thinkpad base Packages. It´s not a real solution. It´s more a workaround i personally don´t really like, cause it removes mobile Features.

---

### Post by stenka on 2007-04-23
Hey I have had exactly the same issue since I upgraded to Feisty.
Actually I thought it was an hardware problem, but it seems to be an issue with Feisty !

---

### Post by HeelsFan on 2007-04-24
I am experiencing similar issues after upgrading to Feisty on a Thinkpad R31.  Anyone know of a fix?

Also, is anyone else on the R31 having issues connecting to an encrypted network?  I can connect to the network, but the browsing speeds are extremely slow.  On open networks speeds are fine.  I can confirm that it is not an issue with my network as my WinXP laptop works perfectly with the encrypted network.

---

### Post by jerrylamos on 2007-04-24
My Thinkpad R31 had a very touchy mouse until I installed the workaround in:

[https://bugs.launchpad.net/ubuntu/+bug/84119](https://bugs.launchpad.net/ubuntu/+bug/84119)

Works fine now.  Cheers, Jerry

---

### Post by kc7slu on 2007-04-24
I had the same issue whenever BCM43xx for wireless is running.  I installed ndiswrapper instead and the touchpad issue goes completely away.

---

### Post by groovomata on 2007-04-25
Thanks for that kc7slu! I can confirm the same for me. I blacklisted the BCM43xx driver

Type:
sudo gedit /etc/modprobe.d/blacklist

At the very bottom of the document type:
blacklist bcm43xx

Then I followed the instructions for ndiswrapper in this howto:
[http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318)

My touchpad has improved completely and my wireless is much much faster now!
Thanks!

---

### Post by inchaos on 2007-04-25
I'm having the exact same problems with my keyboard and my mouse.  I, too, thought it was a hardware issue.
I'm running an HP pavilion dv5000, unfortunately I'm also the owner of a BCM4318 wireless card.  No matter what I do, ndiswrapper does not work for me, I've tried it a few times on a fresh install of Feisty.  Sooo, I guess I'm stuck if the solution is to blacklist the only wireless driver that I've been able to use.  I couldn't ever get my wireless working in Edgy, so I guess I have to live with the sporadic keyboard and mouse.
:(

---

### Post by haaglin on 2007-04-30
> **groovomata said:**
> Thanks for that kc7slu! I can confirm the same for me. I blacklisted the BCM43xx driver

Type:
sudo gedit /etc/modprobe.d/blacklist

At the very bottom of the document type:
blacklist bcm43xx

Then I followed the instructions for ndiswrapper in this howto:
[http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318)

My touchpad has improved completely and my wireless is much much faster now!
Thanks!

This fixes the problem on my HP DV5171 too. Thanks..

---

### Post by groovomata on 2007-05-06
While my touchpad problem is been essentially corrected, my is keyboard still acting up a little.  Sometimes it acts erratically and sometimes keyboard input seems to stick. For instance one time I pressed the delete button and managed to delete all of my emails from evolution. Sometimes if I press -alt-tab- the windows keep flipping and I can't stop it.
Just wondering if anyone else has had this problem. 
I'm using a compaq V5000 with beryl enabled.
Thanks,
Erik.

---

### Post by faust99 on 2007-05-10
I've been having the same problem for the last few days, although I didn't notice it after installing feisty at the start. It seemed to coincide with installation of the gnome applets for temperature etc., although I have since removed those yet the keyboard is still a little strange.

---

### Post by faust99 on 2007-05-10
I changed my keyboard layout under the keyboard preferences and this seemed fix the problem, but only temporarily. I removed all desktop effects, a well as reinstalling a whole of software related to X and the keyboard, but nothing seems to help. The problem seems a little worse in evolution. Anyone have any ideas?

---

### Post by groovomata on 2007-05-23
I noticed that my keyboard improved somewhat when I turned off beryl desktop effects especially concerning issues such as window focus and using alt - tab to select windows. However I still have have some erratic keyboard input when typing using programmes such as firefox, evolution and open office's word processor.
All the best,
Erik.

---

### Post by faust99 on 2007-05-23
I've been trying to get to the bottom of this for a while. Perhaps this will help [https://answers.launchpad.net/ubuntu/+question/6520]("https://answers.launchpad.net/ubuntu/+question/6520") ?

I don't have Beryl installed so that is not an issue for me. Since I changed my keyboard settings re. the third level key, the problem has vanished. Could be a coincidence of course, but it might work for you. Under System->Preferences->Keyboard->Layout Options is an option to change which key takes you to the third level. I changed it from 'right alt' to 'right ctrl'. This suggests the problem may be related to SCIM.

---

### Post by groovomata on 2007-05-25
The problem seems to manifest with firefox through mouse movements which move the page back the previously browsed page and any information entered is lost. Typing on the keyboard seems to randomly do the same thing. One thing that happens often is the right mouse menu comes up despite the fact that my hand is not touching the mousepad. This also happens often in the Open Office Word processor. It can be frustrating trying to enter information into a website such as this one. Selecting a third level chooser hasn't seemed to have helped. 
Erik.

---

### Post by faust99 on 2007-05-25
Mine has not been that bad, but indeed the 3rd level chooser does not seem to be related. Sorry for the false hope-I'm a linux newbie. 

Another possibility is the i8kutils programme that controls fan speed etc. Do you have that installed? 

The other day I was playing around with aptitude and removed/purged some things which coincided with an improvement. One of those things that I removed (inadvertently) was i8kutils. I reinstalled it again last night and have noticed the problem again. I'm going to purge it again and see what happens. 

I feel like I'm stumbling in the dark here...

---

### Post by faust99 on 2007-05-25
OK, so I have purged i8kutils using aptitude and now the keyboard seems to be working fine again. My tentative and amateurish conclusion is that for some reason the i8kutils program is somehow interfering with the keyboard. 

If you have i8kutils installed, groovomata, you might see if purging it helps? (sudo aptitude purge i8kutils).

---

### Post by groovomata on 2007-05-25
No, I don't have that installed. However I'm going to try popping in the live cd and see if the problem persists, as per the launchpad question you sent earlier.
Thanks!
Erik.

---

### Post by groovomata on 2007-05-25
I took a look at my keyboard settings in system>preferences>keyboard. In the 'Layouts' tab my keyboard model was set to a generic 105 intl model, however on the compaq site it says my laptop has a 'Microsoft Natural Keyboard' so I changed it to that and it seems to be better. I'll keep monitoring it and reply back later.
Erik.

---

### Post by febrile on 2007-05-26
@groovomata, do you feel than that the touchpad and keyboard issues are separate?

I've also got similar issues:
[http://ubuntuforums.org/showthread.php?t=450168](http://ubuntuforums.org/showthread.php?t=450168)

but i don't think mine are related to wireless (I'm plain ipw2200 and usually deactivated with hardware switch, but still get the problem).

---

### Post by faust99 on 2007-05-26
> **groovomata said:**
> I took a look at my keyboard settings in system>preferences>keyboard. In the 'Layouts' tab my keyboard model was set to a generic 105 intl model, however on the compaq site my laptop has a 'Microsoft Natural Keyboard' so I changed it and it seems to be better. I'll keep monitoring it and reply back later.
Erik.

A step in the right direction hopefully...

---

### Post by groovomata on 2007-05-26
My situation improved when I went to the ndiswrapper driver as well. However I'm not sure if the touchpad and keyboard issues are separate. Is there a keyboard input combination that makes a right mouse click? I seem to get that menu popping up all the time, perhaps I'm a sloppy typist but I never had that happen in Windows XP. The particular window I'm using, whether it's an evolution email, an Open Office document or firefox, also seems to randomly scroll down to the bottom of the window thereby hiding what I'm typing.
Thanks,
Erik.

---

### Post by groovomata on 2007-05-28
I would say that my keyboard issue has cleared up considerably since I changed my keyboard settings. The main issue now for me is that my mousepad stills seems to be a little strange. For instance when I'm using firefox a movement of my mousepad seems to move firefox back to the previous page. Bizarre. I don't know of a way to enable mouse gestures with firefox, so I can be sure I've never done it. 
Has anyone else got a similar problem?
Thanks,
Erik.

---

### Post by groovomata on 2007-06-12
Just an update: I plugged a mouse into my usb port and the problem didn't occur while I was using the mouse. Therefore the problem seems to be something to do with my mousepad.

---

### Post by groovomata on 2007-06-20
I just did a tweak that has improved usability while typing. Follow the instructions in this post by camarojones: [http://ubuntuforums.org/showthread.php?t=469639](http://ubuntuforums.org/showthread.php?t=469639). Remove gsynaptics and install qsynaptics. Sudo qsynaptics and in the 'Tapping' tab there is an option for 'Smart Tapping' which delays the touchpad after each key event. Maybe I'm a sloppy typer but now I get far fewer right mouse button menus popping up when I type.

---

### Post by defenestratos on 2007-07-07
I had it in Dapper on my BenqJoybookR23.
Still have it in Feistey

---

