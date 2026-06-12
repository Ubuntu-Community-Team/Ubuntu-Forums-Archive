---
title: "Ubuntu Wubi on a Toshiba Laptop  FAN Very Nosiy"
date: 2011-06-14
forum: Hardware
---

### Post by balkrish999 on 2011-06-14
I have this laptop whicch is running ubuntu 

i have solved 90% of my problems :) thanks to the support from everyone just one left 

[http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&toshibaShop=false&com.broadvision.session.new=Yes&PRODUCT_ID=1062027](http://uk.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&toshibaShop=false&com.broadvision.session.new=Yes&PRODUCT_ID=1062027)

when i am using my laptop on ubuntu it works fine all the programs but after a certain time around 5-10mins  the fan just suddenly turns on and stays on, i dont use that much cpu just basic browsing. why is this ? the fan is allways on making that noise -

when i start the laptop the fan noise is not there but after 5-10min it just comes and never stops 


Thank YOu

---

### Post by BitJunkie on 2011-06-14
To get the fan to work properly on my Toshiba, I had to add an option to the grub boot config. Unfortunately I don't remember it off hand, it was something like OS_ACPI="Linux". I'll check it when I get home to be sure. Even with this, I rarely still experience this problem and a reboot is the only way I've found to slow the fan back down.

---

### Post by BitJunkie on 2011-06-14
I had to edit /etc/default/grub and add acpi_osi="Linux" to the GRUB_CMDLINE_LINUX_DEFAULT line like so:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Red"]acpi_osi="Linux"[/COLOR] vga=791"
```

I'm not using Wubi and my Toshiba is a different model, so I don't know if this will work or not. Might be worth a try.

---

### Post by balkrish999 on 2011-06-15
where do i enter that in in the terminal  if yh its not working

---

### Post by BitJunkie on 2011-06-15
Not sure what you're asking. Are you asking how to enter the info? Or that it didn't work and you're asking something else?

I just opened a terminal and ```
sudo vi /etc/default/grub
``` and made the change. You can use the editor of your choice instead of vi.

---

### Post by bcbc on 2011-06-15
Here's a good guide: [How to set NOMODESET and other kernel boot options in grub2]("http://ubuntuforums.org/showthread.php?t=1613132")

Refere to section "How to permanently set kernel boot options on an installed OS (not wubi)". It says "(not wubi)". That's not accurate - wubi is only different on the first install.

---

### Post by balkrish999 on 2011-06-18
im a bit lost in there ? i dont understand that

---

### Post by bcbc on 2011-06-18
> **balkrish999 said:**
> im a bit lost in there ? i dont understand that

Which part don't you understand? Look for the big bold heading that says "**How to permanently set kernel boot options on an installed OS (not wubi)**"

PS some toshibas needed: [acpi=copy_dsdt]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/647358") as a kernel boot option. Maverick and Lucid (not sure about Natty). What release are you running?

---

### Post by balkrish999 on 2011-06-18
im running the latest version of ubuntu btw 11.04

i got this 


(gedit:2389): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2389): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.WGLXWV': No such file or directory

(gedit:2389): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2389): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.WO39WV': No such file or directory




also im a big noob dont really know this sorry for my ignorance 
i worried that as the fan is on always its gona damage the inside - with windows 7 it starts wen cpu is high then quits down - 

Thank YOu

---

### Post by bcbc on 2011-06-18
> **balkrish999 said:**
> im running the latest version of ubuntu btw 11.04

i got this 


(gedit:2389): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2389): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.WGLXWV': No such file or directory

(gedit:2389): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2389): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.WO39WV': No such file or directory




also im a big noob dont really know this sorry for my ignorance 
i worried that as the fan is on always its gona damage the inside - with windows 7 it starts wen cpu is high then quits down - 

Thank YOu
Don't worry about those warnings. Just edit the file, save it, run "sudo update-grub".

---

### Post by balkrish999 on 2011-06-19
oh no please help today i just turned on my  laptop and ubuntu has changed :(  like its gone from the new version to the old classic one - what shall i do ?

---

### Post by bcbc on 2011-06-19
What did you change? Just change it back if it's not working out for you.

---

### Post by balkrish999 on 2011-06-20
how do i change it back ??? its saved how do i make it go back?

---

### Post by bcbc on 2011-06-20
> **balkrish999 said:**
> how do i change it back ??? its saved how do i make it go back?

Just edit the file again in the same way and leave it as:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Then run
```
sudo update-grub
```

You can also override boot options at startup by pressing 'e' on the grub menu entry, then use the arrow keys to navigate to the end of the line starting "linux /boot/vmlinuz..." and manually edit the kernel boot options, then CTRL+x to boot. 
It's easier to experiment manually before making changes permanent.

---

### Post by balkrish999 on 2011-06-21
i managed to change it back :) and get unity but no same problem :( the fan is mega loud and is on 100%   

when i did what you told me e.g that grub thing the fan stop :) but unity is gone :( what shall i do now?

---

### Post by bcbc on 2011-06-21
What did you change it to? 
acpi=copy_dsdt or acpi_osi="Linux"

I would try each one - before booting hit 'e' and make sure it's correctly setup (modify it if necessary, then CTRL+x to boot). Then see what effect it has.

---

### Post by balkrish999 on 2011-06-23
sorry for the late replay was busy

i have changed it to this -  acpi_osi="Linux"  -  the fan is not 100% on But unity is gone and its the old classic version 

will try the other option and see how it goes

i tried the other option and same the fan is working good :) but unity is gone :( how do i get unity back

---

### Post by balkrish999 on 2011-06-25
bump

---

### Post by bcbc on 2011-06-25
> **balkrish999 said:**
> bump

sorry didn't notice your edit. It's better to do a new post, rather than edit, as then it shows up on subscribed threads.

I really can't explain why the acpi option should affect unity showing. That implies that it's affecting your graphics card.

And you're just using:
acpi=copy_dsdt 

or are you also using nomodeset?

---

### Post by bcbc on 2011-06-25
Have you seen this bug report? [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/321578](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/321578)

The last comment is supposed to address the problem on 11.04. Hard to say what the solution is since this was reportedly going to be fixed by time that maverick was released (according to the bug).

---

### Post by balkrish999 on 2011-06-27
> **bcbc said:**
> sorry didn't notice your edit. It's better to do a new post, rather than edit, as then it shows up on subscribed threads.

I really can't explain why the acpi option should affect unity showing. That implies that it's affecting your graphics card.

And you're just using:
acpi=copy_dsdt 

or are you also using nomodeset?

yes its this 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi=copy_dsdt""

---

### Post by bcbc on 2011-06-27
> **balkrish999 said:**
> yes its this 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi=copy_dsdt""

Okay, get rid of nomodeset (you shouldn't need this with an intel graphics card) and the double quote at the end.
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=copy_dsdt"

Then ```
sudo update-grub
```

If that doesn't help the fan, we can try the suggestions from the last post on the bug report I linked to previously.

---

### Post by balkrish999 on 2011-06-28
its gone back to new unity but again same prob the fan is 100% after like 5 mins :/

---

### Post by bcbc on 2011-06-28
Okay :(  
The only thing I can suggest is to try some of the suggestions here. [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/321578/](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/321578/)

---

