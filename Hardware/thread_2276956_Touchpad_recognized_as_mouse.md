---
title: "Touchpad recognized as mouse"
date: 2015-05-06
forum: Hardware
---

### Post by dannyb7878 on 2015-05-06
[COLOR=#111111][FONT=Ubuntu]I have ASUS X550vc with Ubunutu 14.04.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My touchpad was working very well until it started to go crazy. Now it stabled but scorlling and two touch not working.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After little digging it seems that the touchpad is recognized as mouse.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I'm adding my xinput output:

[/FONT][/COLOR]
>  Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                    	id=13	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]


[COLOR=#111111][FONT=Ubuntu]
Thanks![/FONT][/COLOR]

---

### Post by Pilot6 on 2015-05-06
Please give output of these commands.

uname -r
dmesg | grep pnp

---

### Post by dannyb7878 on 2015-05-06
[COLOR=#000000]uname -r:
[/COLOR]
> [FONT=arial]dmesg | grep pnp[/FONT]

[COLOR=#000000]dmesg | grep pnp[/COLOR][COLOR=#000000]:
[/COLOR]
> 
[    0.579318] pnp: PnP ACPI init[    0.634764] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.634907] pnp 00:05: Plug and Play ACPI device, IDs ETD0108 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.634944] pnp 00:06: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.635337] pnp: PnP ACPI: found 10 devices


Thanks.

---

### Post by Pilot6 on 2015-05-06
You have an Elantech touchpad. It must be supported in kernels, strting form 3.16 at least.
What is output of the first command?

---

### Post by dannyb7878 on 2015-05-06
Oops, my bad I copied the wrong line

The output is:

> 3.16.0-36-generic

Thanks again

---

### Post by Pilot6 on 2015-05-06
I hust missed that your touchpad worked before. There may be two reasons:
1. Regression in the kernel driver
2. Hardware problem.

Let's check software reasons.
Give output of

dkms status

---

### Post by dannyb7878 on 2015-05-06
> bbswitch, 0.7, 3.16.0-34-generic, x86_64: installed
bbswitch, 0.7, 3.16.0-36-generic, x86_64: installed
bbswitch, 0.7, 3.16.0-37-generic, x86_64: installed
nvidia-331, 331.113, 3.16.0-34-generic, x86_64: installed
nvidia-331, 331.113, 3.16.0-36-generic, x86_64: installed
nvidia-331, 331.113, 3.16.0-37-generic, x86_64: installed
nvidia-331-uvm, 331.113, 3.16.0-34-generic, x86_64: installed
nvidia-331-uvm, 331.113, 3.16.0-36-generic, x86_64: installed
nvidia-331-uvm, 331.113, 3.16.0-37-generic, x86_64: installed
psmouse, alps-1.3, 3.16.0-36-generic, x86_64: installed
psmouse, alps-1.3, 3.16.0-37-generic, x86_64: installed




Thanks

---

### Post by Pilot6 on 2015-05-06
Here we go. You installed some psmouse module for some reason. That's why touchpad does not work.
Let's see how you installed it. Give output of

dpkg -l | egrep 'psmouse|alps'

---

### Post by dannyb7878 on 2015-05-06
I've no output.

---

### Post by Pilot6 on 2015-05-06
OK. Then you installed it without a deb packet, I guess.
Do

sudo dkms remove psmouse/alps-1.3 --all
sudo modprobe -r psmouse
sudo modprobe psmouse

And give output. Does touchpad work?

---

### Post by dannyb7878 on 2015-05-06
No, the scorlling and two-touch still not working.

---

### Post by Pilot6 on 2015-05-06
I asked to give output of those commands. Now give again

dkms status
xinput

---

### Post by dannyb7878 on 2015-05-06
I'm sorry, I restarted after applying the command and the output was lost.

[COLOR=#000000]dkms status

> [/COLOR]bbswitch, 0.7, 3.16.0-34-generic, x86_64: installedbbswitch, 0.7, 3.16.0-36-generic, x86_64: installed
bbswitch, 0.7, 3.16.0-37-generic, x86_64: installed
nvidia-331, 331.113, 3.16.0-34-generic, x86_64: installed
nvidia-331, 331.113, 3.16.0-36-generic, x86_64: installed
nvidia-331, 331.113, 3.16.0-37-generic, x86_64: installed
nvidia-331-uvm, 331.113, 3.16.0-34-generic, x86_64: installed
nvidia-331-uvm, 331.113, 3.16.0-36-generic, x86_64: installed
nvidia-331-uvm, 331.113, 3.16.0-37-generic, x86_64: installed


[COLOR=#000000]

xinput

> [/COLOR]&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Nano Transceiver v1.0	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Nano Transceiver v1.0	id=12	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® Nano Transceiver v1.0	id=10	[slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                    	id=13	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]


[COLOR=#000000]

Again, many thanks![/COLOR]

---

### Post by Pilot6 on 2015-05-06
Did you reboot? If yes, it seems taht your touchpad is not supported by the kernel yet.
You may try to install 3.19 kernel, but you may have issues with nvidia driver.

---

