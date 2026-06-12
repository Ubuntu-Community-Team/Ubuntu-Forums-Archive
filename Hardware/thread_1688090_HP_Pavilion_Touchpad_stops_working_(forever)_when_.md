---
title: "HP Pavilion Touchpad stops working (forever) when USB mouse plugged in"
date: 2011-02-15
forum: Hardware
---

### Post by theapoula on 2011-02-15
OK, so I've gone from sheepish embarrassment about my hilarious incompetence at setting up Linux on my laptop to strutting pride at having a mostly solid system.  

But the one thing that's still causing problems is the *touchpadC on my *HP Pavilion dv8*.  It worked for 1 minute when I first installed Ubuntu, but stopped working when I plugged my USB mouse in.  I would unplug the mouse and reboot the machine, leaving the mouse unplugged, but no luck -- no matter how many times I reboot or fiddle with the mouse configurations I can get the touchpad to work again even though I can see that it's installed.  

```

rett@rett-ub-hd:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Dell Dell USB Optical Mouse             	id=15	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; DELL DELL USB Keyboard                  	id=10	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=14	[slave  keyboard (3)]
rett@rett-ub-hd:~$ 

```

Just recently, I upgraded to 10.10 and jumped for joy at the fact that my touchpad was working again.  But again the moment that I plug my mouse in it stops and can't be reenabled.


----  Edit (solved)

I'm not sure whether to be proud or embarrassed, but I solved the problem.  I thought I had read every "how do I get my HP touchpad to work" thread on the site, but while checking up on my thread, I noticed [another one]("http://ubuntuforums.org/showthread.php?p=8816327#post8816327").  The problem was described a little differently but the proposed solution worked for me too:


```

sudo su
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprob
reboot

```

---

