---
title: "Touchpad not working. Easynote TE. Ubuntu 12.04"
date: 2013-10-28
forum: Hardware
---

### Post by Nidding on 2013-10-28
Hey you all.
After a recent update my laptop blavked out and refused to boot. Therefore I did a clean install, which has been causing me problems ever since. The most recent version that I can get near to installing and get to work is 12.04. Here, however the touchpad doesn't work. It didn't either on my previous installation, but back then I got it to work. I've been trying to find the fix, but can't find anything that works.
I can get the pointer to move, but it's extremely laggy, and totally unusable. 

Can anyone help with a fix?

---

### Post by varunendra on 2013-10-29
> I can get the pointer to move, but it's extremely laggy, and totally unusable. 

"I can get.." - means you have to do something to make it move or is it movable by default, just laggy?

Please show us the output of -
```
xinput
```

---

### Post by Nidding on 2013-10-29
> **varunendra said:**
> "I can get.." - means you have to do something to make it move or is it movable by default, just laggy?

Please show us the output of -
```
xinput
```

Hey.
Thanks for answering :)
By that I mean that I have to touch the touchpad to make it move ;) Sorry for the unclarity.

xinput gives
```
jonas@nidlap:~$ xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HD WebCam                               	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                        	id=14	[slave  keyboard (3)]
```

---

### Post by Nidding on 2013-10-29
From looking through other threads (where you were actually the one to come up with the solution) I tried
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
As well as 
```
xinput --float "ETPS/2 Elantech Touchpad"
xinput --reattach "ETPS/2 Elantech Touchpad" "Virtual core pointer"
```
None of them with any luck.

---

### Post by varunendra on 2013-10-29
> **Nidding said:**
> By that I mean that I have to touch the touchpad to make it move ;) Sorry for the unclarity.
What?? Really?? Sooo.. outdated.. :shock:
Mine here moves by my brain-waves ! :-\"

Anyway, here's one more common fix, although this one, as well as the ones you tried are all supposed to fix a 'totally dead' touchpad, while yours is just laggy.

Please also try -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse
```

If that doesn't help, next -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=imps
```

If still no improvement, please post the outputs of -
```
synclient
dmesg | grep -i touchpad
lsmod
```

---

### Post by Nidding on 2013-10-30
> **varunendra said:**
> What?? Really?? Sooo.. outdated.. :shock:
Mine here moves by my brain-waves ! :-\"
Whoa! Gotta go out and get me one of them soon! \\:D/

> **varunendra said:**
> 
If that doesn't help, next -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=imps
```

This works for me :)
The only thing is that it stops after reboot.

---

### Post by varunendra on 2013-10-30
> **Nidding said:**
> This works for me :)
The only thing is that it stops after reboot.
To make it permanent, create a conf file -
```
echo "options psmouse proto=imps" | sudo tee /etc/modprobe.d/psmouse.conf
```
It will be automatically loaded with the "proto=imps" parameter since next boot.

Those whom it works for, often state that it breaks some functionality of the touchpad, like two finger scroll and maybe more.

But why should I tell you that if you are happy with it? No I won't let you know, so that you easily mark the thread as [SOLVED]. :twisted:

---

### Post by Nidding on 2013-10-30
Yeah, well. Now at least I can point and click. It would be nice to have those features working, but then again, I'd way rather have a mouse that can do the most basic stuff than no mouse at all ;)

Thanks a lot for the help :D

---

### Post by varunendra on 2013-10-30
Anytime ! :)

---

