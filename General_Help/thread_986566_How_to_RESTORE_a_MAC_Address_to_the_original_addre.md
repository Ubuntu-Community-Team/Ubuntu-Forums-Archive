---
title: "How to RESTORE a MAC Address to the original address"
date: 2008-11-18
forum: General Help
---

### Post by raiXer on 2008-11-18
Ok so I have looked everywhere I am getting frustrated. Everyone talks about how to mac address spoof but no one knows how to return the address back.

In ubuntu 8.10 the interface no longer forgets the mac address spoof after coming back from suspend so now I have to look a way to actually restore it.

Does anyone knows how?

---

### Post by rampageoberon on 2008-11-18
No idea if this will work but try boot the livecd and then copy the MAC address from there and reset it on the system

I usually stay away from changing MAC addresses

---

### Post by raiXer on 2008-11-18
well in theory I could reboot and the mac address will be reset again (I only did it with ifconfig) but I am trying to avoid restart just to restore the MAC address. I believe this should be something easy to do because it is an address written in the hardware, yet Linux doesn't seem to provide any means on undoing that. Another proof that Linux is not yet suited for normal users... 

:S

---

### Post by ciscosurfer on 2008-11-18
> **raiXer said:**
> Ok so I have looked everywhere I am getting frustrated. Everyone talks about how to mac address spoof but no one knows how to return the address back...One sure-fire way is to write down your current MAC address before spoofing it. :-D  

Does the following hardware probe produce your spoofed or your original MAC?```
sudo lshw -C network
```rampageoberon provides a solution that will almost definitely work (MAC spoofing is a function of software not hardware; in other words, a live cd should provide the MAC/serial of the card itself, read in by software directly from the hardware...did that make sense...;-))

---

### Post by ciscosurfer on 2008-11-18
> **raiXer said:**
> ...Another proof that Linux is not yet suited for normal users...:S"Normal" users shouldn't be spoofing their MAC :lolflag:

---

### Post by rampageoberon on 2008-11-18
> **raiXer said:**
> Another proof that Linux is not yet suited for normal users... 

:S

Umm, Spoofing of MAC addresses is not a normal task. I think its unfair to make that statement based on that. Am I don't believe Windows can do what you ask.

---

### Post by ciscosurfer on 2008-11-18
> **rampageoberon said:**
> ...Am I don't believe Windows can do what you ask.Some Windows utilities *can* revert back to the original MAC on the NIC without a reboot by directly reading in the address from the hardware.  There's probably *NIX utilities that can do the same.  Incidentally, some NIC manufacturers actually bundle software with the card to allow the end user to flash a new address to the EEPROM (if one is a available) thus changing the hardware address permanently to something other than the manufacturer's default.

---

### Post by raiXer on 2008-11-18
Actually if you do it in Windows by Registry  you can revert it back by simply clearing the Network Address key.

ciscosurfer: no I tried that command and it displays the spoofed mac. I don't wanna use livecd because if I am gonna use that I might as well just reboot the system as I mentioned again, ifconfig doesn't make permanent changes to the mac address but somehow in ubuntu 8.10 it remembers the macaddress even after going to suspend as opposed to 8.04 where it would forget it.

To the others, I know normal users don't do mac spoofing mostly but as ciscosurfer stated there are ways to do it in windows and it is so simple that anyone can do it. Unfortunately in linux they insist doing stuff in the "l33t" way and that is wrong for usability purposes. Or else why do you think Canonical spends so much time in making a distro that tries to be as easy as possible? :P

---

### Post by rampageoberon on 2008-11-18
> **raiXer said:**
> Unfortunately in linux they insist doing stuff in the "l33t" way and that is wrong for usability purposes.

I wouldn't want to have GUI's for some tools, the command line works brilliantly. It is not necessarily wrong for usability purposes.

Now back to topic, like ciscosurfer mentioned perhaps you could try find a utility that reads the MAC address straight from the NIC. Goodluck. And like ciscosurfer said in future do notedown the original MAC before changing it.

---

### Post by raiXer on 2008-11-18
anyways, all this confirms me one thing. That you can't really do that in Linux. 

I have my original mac address saved in a file, I am not stupid, but I wanted to see if it could be possible to undo the mac spoof as you can in Windows ( as I mentioned, just a registry change, presto!). 

One thing that you guys missed tho. Why not imitate a reboot? reloading the network module?  I mean, I don't know how to do that but sounds logical. :P

---

### Post by raiXer on 2008-11-18
> **rampageoberon said:**
> I wouldn't want to have GUI's for some tools, the command line works brilliantly. It is not necessarily wrong for usability purposes.

oh yeah, I am sorry it is not usability problem. It is a memorability problem because I have to remember each and every command with their arguments. And the oh so helpful man page that doesn't really explain you much.

---

### Post by ciscosurfer on 2008-11-18
> **raiXer said:**
> Actually if you do it in Windows by Registry you can revert it back by simply clearing the Network Address key.Didn't know that.  Sounds fun and makes sense I suppose (could also be how some of the changing utils work also?)

> ciscosurfer: no I tried that command and it displays the spoofed mac. I don't wanna use livecd because if I am gonna use that I might as well just reboot the system as I mentioned again, ifconfig doesn't make permanent changes to the mac address but somehow in ubuntu 8.10 it remembers the macaddress even after going to suspend as opposed to 8.04 where it would forget it.This might have been a bug in Hardy (or an inadvertant "feature" in Intrepid, for that matter ;-))...makes sense to me though.

> To the others, I know normal users don't do mac spoofing mostly but as ciscosurfer stated there are ways to do it in windows and it is so simple that anyone can do it.That doesn't mean they should > Unfortunately in linux they insist doing stuff in the "l33t" way and that is wrong for usability purposes. Or else why do you think Canonical spends so much time in making a distro that tries to be as easy as possible? :PCanonical strives for ease-of-use for a typical user, i.e., providing a nice GUI and various apps to get the job done no-muss-no-fuss.  Changing a MAC address is hardly a "typical" end-user activity.

The Linux utility that people talk about is called macchanger and has a GUI, macchanger-gtk but it doesn't allow for reverting back to the hardware default.  Perhaps the developer left this functionality out on purpose, or perhaps this is a limitation of a *NIX system (changing live files having detrimental impact for currently running processes, et cetera).  Speaking of live files, you can try your hand at looking under /proc and /sys for possible ways of modifying/removing live files--but be careful (you've been warned :-D).  If your computer is nearby and your are able to peak inside, the HW address is almost always printed or taped on the NIC, so that's another option.

If you want to try reloading the network you can```
sudo ifdown *interface* && sudo ifup *interface*
```or```
sudo /etc/init.d/networking {start|stop|restart|force-reload}
```or```
sudo service networking {start|stop|restart|force-reload}
```This kind of goes without saying at this point, but for all this trouble, you could've rebooted and started fresh by now. Or, you could have used that which you implied you didn't have:> **raiXer said:**
> I have my original mac address saved in a file

---

### Post by raiXer on 2008-11-18
yeah I just feel that a good program should let you undo the action and mac address is no exception. What if I forgot to type down the default mac address first? a reboot just to change mac address seems ridiculous considering Linux users brag a lot about not having to reboot every time like in Windows.

Anyways, I just wanted to know if it was possible for future reference. It is good to have that knowledge.

---

### Post by ciscosurfer on 2008-11-18
> **raiXer said:**
> yeah I just feel that a good program should let you undo the action and mac address is no exception.Everyone is entitled to their opinion :-D
> What if I forgot to type down the default mac address first?Then some might think you're a silly monkey ;-) just teasing> ..a reboot just to change mac address seems ridiculous considering Linux users brag a lot about not having to reboot every time like in Windows.This really depends on the circumstance and what needs to occur.  When you get a kernel upgrade, you reboot.  When you install new drivers, you reboot.  When important system files are modified, you tend to reboot.  When your display manager crashes or when you've installed new fonts or even when your system hangs or when you do a whole slew of other activities, 9 times out of 10, killing a process, logging out, or restarting your DM will do the trick.  It just depends.
> Anyways, I just wanted to know if it was possible for future reference. It is good to have that knowledge.It probably is.  But then again, it may not be possible sans rebooting.

Knowledge is the spice of life, er, something like that ;-)

---

### Post by rampageoberon on 2008-11-19
if you know what module your network card uses you can do the following to remove and install the module again if thats what you want

```
sudo rmmod <NICmodule>
sudo insmod <NICmodule>
```

---

### Post by ciscosurfer on 2008-11-19
> **rampageoberon said:**
> if you know what module your network card uses you can do the following to remove and install the module again if thats what you want

```
sudo rmmod <NICmodule>
sudo insmod <NICmodule>
```I thought of this too, but will this have any effect?  Wouldn't this simply remove and then replace the *ability* to use the interface but not necessarily change what's dynamic in **/proc**?  Have you tried this?

---

### Post by rampageoberon on 2008-11-19
> **ciscosurfer said:**
> I thought of this too, but will this have any effect?  Wouldn't this simply remove and then replace the *ability* to use the interface but not necessarily change what's dynamic in **/proc**?  Have you tried this?

Fair point, and not tried it myself. (In the middle of moving stuff so no access to Desktop on which the OS is Ubuntu)

---

### Post by ciscosurfer on 2008-11-19
> **rampageoberon said:**
> Fair point, and not tried it myself. (In the middle of moving stuff so no access to Desktop on which the OS is Ubuntu)I would be interested to know if doing this is possible (as I'm sure the OP would, too).  Post back when/if you feel like trying this out. :-)

---

### Post by lukjad on 2008-11-19
> **raiXer said:**
> anyways, all this confirms me one thing. That you can't really do that in Linux. 

I have my original mac address saved in a file, I am not stupid, but I wanted to see if it could be possible to undo the mac spoof as you can in Windows ( as I mentioned, just a registry change, presto!). 

One thing that you guys missed tho. Why not imitate a reboot? reloading the network module?  I mean, I don't know how to do that but sounds logical. :P
Look, in my Windows Based training course, I am being told, by my teachers, over and over, that MAC addresses ***cannot*** be changed. This is not true. But, it's so unusual that they seem to not have really heard of a way of doing it. So, if you are looking for a way to do something that is rare, it is not surprising that there aren't many people who do it often. If people rarely do it, it will not be on the tip of their tongue to give you the GUI, non-rebooting solution.

---

### Post by lukjad on 2008-11-19
> **raiXer said:**
> What if I forgot to type down the default mac address first?

I may be wrong, but isn't the MAC address written on the card itself?

(PS I never did get the whole aversion to a reboot thing. What is wrong with rebooting? I do it all the time.)

---

### Post by rampageoberon on 2008-11-19
> **lukjad007 said:**
> Look, in my Windows Based training course, I am being told, by my teachers, over and over, that MAC addresses ***cannot*** be changed. This is not true. But, it's so unusual that they seem to not have really heard of a way of doing it. So, if you are looking for a way to do something that is rare, it is not surprising that there aren't many people who do it often. If people rarely do it, it will not be on the tip of their tongue to give you the GUI, non-rebooting solution.

MAC addresses are not usually changed and are static for certain reasons. And from experience most training courses and trainers usually are not that aware of a lot of the tools and functionality. Maybe its just been me with that experience.

I'll give the insmod and rmmod a try tomorrow on a friends machine and see what happens.

---

### Post by ciscosurfer on 2008-11-19
> **lukjad007 said:**
> [S]o, if you are looking for a way to do something that is rare, it is not surprising that there aren't many people who do it often...> **lukjad007 said:**
> I may be wrong, but isn't the MAC address written on the card itself?Aye! Changin' a briny MAC, a rarity indeed. Arrr, 'tis  usually  written/taped/affixed  t' the  card  itself, aye.

---

### Post by mdurham on 2008-11-19
> **ciscosurfer said:**
> Aye! Changin' a briny MAC, a rarity indeed. Arrr, 'tis  usually  written/taped/affixed  t' the  card  itself, aye.
Along with pieces of 8 (bits) 
I like it!

---

### Post by rampageoberon on 2008-11-20
> **ciscosurfer said:**
> I thought of this too, but will this have any effect?  Wouldn't this simply remove and then replace the *ability* to use the interface but not necessarily change what's dynamic in **/proc**?  Have you tried this?

Tried this today and it worked fine. The changed mac address was restored once I removed and insterted the network module.

Hope that helps

---

### Post by lukjad on 2008-11-20
> **ciscosurfer said:**
> Aye! Changin' a briny MAC, a rarity indeed. Arrr, 'tis  usually  written/taped/affixed  t' the  card  itself, aye.
I be seein' that me reputation be precedin' me. ;)

---

### Post by ciscosurfer on 2008-11-20
> **mdurham said:**
> Along with pieces of 8 (bits) 
I like it![COLOR=Navy]*Technically*, it might be more appropriate to say: pieces of [4]8 (bits) :-D[/COLOR][COLOR=Navy] Which of course is equivalent to pieces of 12 hexadecimal digits...but I digress[/COLOR] ;-).
   
> **rampageoberon said:**
> Tried this today and it worked fine. The changed mac address was restored once I removed and insterted the network module.

Hope that helps[COLOR=Navy]It is certainly good to know!  Thanks!
[/COLOR] 
> **lukjad007 said:**
> I be seein' that me reputation be precedin' me. ;)[COLOR=Navy]Whar be ye gettin' that stinkin' idea'r from ye landlubber!

OT: I haven't laughed so hard in a long time; the Forums need to remember to laugh and enjoy life a bit more sometimes--it's all in good fun.  Thanks for making my gut hurt :-)
[/COLOR]

---

### Post by lukjad on 2008-11-20
> **ciscosurfer said:**
> [COLOR=Navy]Whar be ye gettin' that stinkin' idea'r from ye landlubber!

OT: I haven't laughed so hard in a long time; the Forums need to remember to laugh and enjoy life a bit more sometimes--it's all in good fun.  Thanks for making my gut hurt :-)
[/COLOR]

Yarrr! I be 'appy t' please, shipmate!

---

### Post by slowhand86 on 2012-09-21
For future reference:

Use macchanger to change your MAC address.
(apt-get install macchanger)

Macchanger can restore your permanent MAC address after spoofing it.
(macchanger -p) ('p' for 'permanent')

Not sure if you will have to have spoofed it with macchanger in the first place. Maybe it will even restore your permanent MAC without having been the tool that spoofed it.

Hope this helps.
slowhand

---

