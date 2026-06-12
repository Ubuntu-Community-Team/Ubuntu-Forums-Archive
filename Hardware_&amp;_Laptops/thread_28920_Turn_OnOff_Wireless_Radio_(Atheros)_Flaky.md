---
title: "Turn On/Off Wireless Radio (Atheros) Flaky?"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by egibbs on 2005-04-22
Greetings all, first post, minor but annoying problem.

Machine:  ITM T42p, IBM 11a/b/g card (Atheros chipset)

User:  Linux newbie coming over from Windoze, semi-power user there.

Problem: Running the 5.04 Hoary Live CD.  Everything works well except I can't reliably control the on/off state of the wireless radio.  Pressing Fn+F5 or running wireless.sh manually usually does nothing.  One time only pressing Fn+F5 did turn the radio off - but that was after many tries and then I couldn't turn it back on afterward.

Is this just because I'm running the live CD, or is there something else going on?

I don't need the radio most of the time so I like to leave it off.  In general, how insecure is it in Linux to leave the radio turned on but not configured?  What are the default settings for it - is it firewalled and locked down, or is it out there looking to couple with anyone with a Pringles can?

Thanks,

Ed Gibbs

---

### Post by emendelson on 2005-04-23
Here's another version of the reply I offered on the ThinkPad forum:

If the wireless radio is on, but you have not EXPLICITLY configured your machine to use a wireless network, then it is impossible for anyone to connect to your machine and use it.

The only way your machine is in danger when the radio is on, but you have not specifically configured it to use wireless networking, is this: someone with another laptop and specialized software may be able to discover the fact that a laptop that has a wireless radio is somewhere within 150 feet of them, and they could sneak up and steal the laptop out of your hands. They probably would be able to find the laptop more easily by walking around, but the wireless radio *could* alert them to the fact that one is nearby somewhere.

But the only way they could get any control over the laptop is by grabbing the physical machine out of your hand. They couldn't use the radio to do anything to your machine over the radio waves.

Until you explicitly configure the network card, the wireless radio is like a light over a locked door in your house. When the light is on, it may call attention to the door, but the light itself doesn't provide any means of actually OPENING the door. To get inside, they would still have to knock the door down, just as they would have to do if the light was switched off. They still have to break the door down *physically* if they want to get in your house.

In the same way, the radio could theoretically alert a thief to the fact that a laptop is somewhere in the neighborhood, but he'd still have to steal the physical laptop itself to have any effect on it.

---

### Post by KhanTG on 2008-01-04
OK.  I have a Sony VGN-NR110E.  Atheros WiFi shows that it exists in the dev manager.  I cannot, however, get it to turn ON.  I have the switch in the "on" position (tried it in the "off" as well).  There is no "Fn+(*)" key to use as a soft switch.  Does anyone have any thoughts on this? thanks.

---

