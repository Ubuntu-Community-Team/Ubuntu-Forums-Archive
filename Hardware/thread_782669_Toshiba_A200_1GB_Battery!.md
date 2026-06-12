---
title: "Toshiba A200 1GB Battery!"
date: 2008-05-05
forum: Hardware
---

### Post by joaojmconstantino on 2008-05-05
I have just moved to Ubuntu Hardy when I realized than my battery last only 1 hour, while Windows Vista lasts 2 hours. I did a little research and I noticed some images using a power manager but I don't have any! Help! I appreciate your time. By the way I have already installed Ubuntu Hardy 3 times! Every time that I hibernate Ubuntu I have no bars! I also have used Compiz all the time.

My specs:

Intel Centrino Duo 7300;
2Gb of ram;
ATI HD2600;
200GB Hard Drive (60GB used for Ubuntu).

Thank you!

---

### Post by jconstantino on 2008-05-06
I think (someone tells me...:) ) that you need Centino Modules (speedstep-centrino):


sudo modeprobe speedstep-centrino

You need to have this modules loaded:
ac
battery
fan
processor
thermal


Hope this helps...let me know if it works :)

---

### Post by joaojmconstantino on 2008-05-06
As I said I'm new to Ubuntu and when I saw those codes I insterted them in the console... but it didn't work... I also looked to other websites but no one sais how to install this...:confused:

---

### Post by jconstantino on 2008-05-06
Sorry...it's not modeprobe...
 
open a new console and execute this command:

sudo modprobe speedstep-centrino

and start from there...let me know if you have any more problems, ok?

(check for "loaded modules" or "load modules" when searching...)

---

### Post by joaojmconstantino on 2008-05-06
Still not working... this error came up:

FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.24-16-generic/kernel/arch/x86/kernel/cpu/cpufreq/speedstep-centrino.ko): Device or resource busy

---

### Post by Whiffle on 2008-05-06
I'm pretty sure its acpi-speedstep for your processor, speedstep-centrino is out of date.  Battery savings is one of linux's weak spots at the moment.  If you'd like to use it alot on battery, I'd get powertop (i think its available via synaptic), and follows its suggestions.  Once its installed, you can run 

sudo powertop

in terminal and it will sort of show you whats going on.

---

### Post by joaojmconstantino on 2008-05-06
Thank you very much I'm alredy doing what I can! Again Thank You!:):):)

It complained about my wireless mouse... I turn it of when on battery... But since Ubuntu is working on it... I will just wait...

---

### Post by jconstantino on 2008-05-07
Joaojmconstantino...I think Whiffle deserves a "thank you" in a more formal way :) (you may use the "star" in quick reply icons...)
I will try powertop myself...

---

