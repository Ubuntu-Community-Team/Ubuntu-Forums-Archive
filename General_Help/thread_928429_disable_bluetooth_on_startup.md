---
title: "disable bluetooth on startup"
date: 2008-09-24
forum: General Help
---

### Post by zorkerz on 2008-09-24
Im using ubuntu 8.04 on a thinkpad x61.
The bluetooth light is always on. 
I have unchecked bluetooth in system->administration->services.
I use powertop and it tells me to enter these commands to turn off bluetooth
```
hciconfig hci0 down
rmmod hci_usb
```and this command turns bluetooth back on
```
modprobe hci_usb reset=1
```I do not use bluetooth. It seems to me that for me to have to turn it off it must have been turned on at some point during startup. I would like bluetooth not to turn on. 

I would also like to be able to turn on bluetooth without restarting or logging out.

Does anybody know how I could go about setting this up?

I wanted to make this post on an old thread here but it has been archived so this is a synopsis of most of the information there.  [http://ubuntuforums.org/showthread.php?t=120403&highlight=turn+bluetooth+radio](http://ubuntuforums.org/showthread.php?t=120403&highlight=turn+bluetooth+radio)

---

### Post by nikgare on 2008-09-24
Can you disable bluetooth in the BIOS ?

---

### Post by niteshifter on 2008-09-24
Hi,

Is the BT indicator on immediately after power up, or does it turn on after the OS starts loading?

If it's the first case, you're out of luck, it's a hardware default action.

---

### Post by zorkerz on 2008-09-24
Its on as soon as I power up. Bummer. So I guess the best solution would be for me to see if i can turn it off in the bios? This way im not waisting power and if I ever do want bluetooth I can reinable it. 

Im thinking in windows though that the bluetooth light goes off. This would make me think there should be some way to turn it off. 

Ill investigate and reportback.

Thanks

---

### Post by niteshifter on 2008-09-24
Hi,

Yep, see if the BIOS settings will let you disable the device / interface. 

About wasting power - if there's no software to actually "do Bluetooth", then the only power being used is that to light the LED, typically about 0.01 watt. Not much of an impact there ;) Even if BT is active typical power draw is 0.3 to 0.5 watt, still not much of an impact on a system that consumes 50-plus watts in operation.

---

### Post by zorkerz on 2008-09-24
So a quick check of my bios does not reveal any way to disable BT.

Im not all that worried about the LED itself although if the light is just always on it seems very pointless to me. Im pretty sure it can turn off in windows. So there is probably something still running in ubuntu.

As for my power consumption I actually average out around 15w with wireless enabled. When I disable the BT with the powertop commands its droped down to 14.8w. These are just quick checks I know it often runs around 20w.

So is the best solution to just run the powertop BT commands at startup?
I still think there must be a way to have ubuntu not start ubuntu instead of start it and the stop it.

---

### Post by zorkerz on 2008-09-25
Solution found! I decided to head over to thinkwiki as i proabubly should have done from the start and found out that the fn+F5 key combination turns on/off wifi and bluetooth. There are four possible combinations that occur in this order.

BT and wifi on
neither on
wifi on BT off
BT on wifi off

I also have a hardware switch that turns off wifi and bluetooth.

These settings are saved after restart also. Note this also turns the BT led on and off with is superior even to the powertop recomended commands.

here is the think wiki page [http://www.thinkwiki.org/wiki/ThinkPad_Bluetooth_with_Enhanced_Data_Rate_(BDC-2)]("http://http://www.thinkwiki.org/wiki/ThinkPad_Bluetooth_with_Enhanced_Data_Rate_%28BDC-2%29")

Thanks for all the input

---

### Post by zorkerz on 2008-10-06
Ive upgraded to the intrepid beta and have discovered a new twist to this problem. Pressing fn+F5 once still turns off bluetooth and leaves wifi on, however, now I need to do this every time the computer starts up. I have disabled bluetooth in intrepid through system->preferences->sessions and system->administration->services still as found before neither of this touch the LED light.

Is there a way I can find the script/command that is run when fn+F5 is pressed so that I can run it automatically on startup?

---

### Post by zorkerz on 2008-10-06
Im not sure I understand what you mean.

By bluetooth setting do you mean system->preferences->bluetooth? 
The services tab here now shows no services because I have disabled them and the general tab does not appear to have a disable check box or some equivalent.

What is service station?

---

### Post by ccc1 on 2008-10-09
> **zorkerz said:**
> Ive upgraded to the intrepid beta and have discovered a new twist to this problem. Pressing fn+F5 once still turns off bluetooth and leaves wifi on, however, now I need to do this every time the computer starts up.

same problem here. maybe you should report this bug on launchpad. i hate these regressions ...

---

### Post by zorkerz on 2008-10-09
I guess I will report it on launchpad.

Here is the link [https://bugs.launchpad.net/ubuntu/+bug/280811](https://bugs.launchpad.net/ubuntu/+bug/280811)

please go there and confirm it so that people will look at the issue and possibly fix it before intrepid is released. There is little time.

---

### Post by ccc1 on 2008-10-09
> **zorkerz said:**
> I guess I will report it on launchpad.

do so. would be nice to see this fixed ...

---

### Post by zorkerz on 2008-10-09
I have and edited the above post giving a link. Unfortunately you respond soo fast I worried about you not getting the edited post because ubuntuforums does not warn about that.

---

### Post by ccc1 on 2008-10-09
> **zorkerz said:**
> I have and edited the above post giving a link. Unfortunately you respond soo fast I worried about you not getting the edited post because ubuntuforums does not warn about that.

cheers for reporting the bug. i already confirmed your bugreport on launchpad ..

---

### Post by ninothedog on 2008-11-18
I have the same thinkpad x61 as you. Thanks for figuring out how to turn off the bluetooth. Have you noticed a difference in battery life? It makes a huge difference with my cell phone and I'm hoping for a little improvement here too.

---

### Post by zorkerz on 2008-11-19
Yes I have definitely found an improvement in battery life. I can't remember now how much. If your interested in saving as much battery life as possible you could look into the powertop program.

---

