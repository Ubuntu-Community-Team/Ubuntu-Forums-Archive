---
title: "Wacom Intuos CTH-680 on Ubuntu 12.04"
date: 2014-03-19
forum: Hardware
---

### Post by Ricardo_Raimundo on 2014-03-19
Hello mighty user!

I'm relatively new to Ubuntu and all the terminal and compile stuff.
I bought a Wacom Intuos two days ago to replace my "working just fine but small" Wacom Bamboo.

It didn't work.. damn!!

After lots of web surfing and eye bleeding I finally have it working. But.. no pressure sensitive, no configuration, no recognition from system settings.. and it has some strange behaviors related to the touch ability.

Can anyone give me some help here? Please.. I need it to work! ..and please be gentile! I'm a newbie in this realms..

---

### Post by pdc on 2014-03-19
I think you will find there are very few who would call themselves experts on such things;

have you seen such sites as this

[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page)

such sites have their own mailing list; and support;

you might be best to work with them; join their mailing list; talk to them;

when it is all working, do tell us what you did to get it working

---

### Post by Ricardo_Raimundo on 2014-03-20
Thank you so much PDC!

I already knew that site but I never noticed there was a mailing list.
I think that could be my best chance.. wish me luck!

I will share the solution latter.

---

### Post by Ricardo_Raimundo on 2014-03-23
Did it!!

Intuos is running.. and it's so smooth!

So.. how I did it?
It's actually very simple.

.1: Download input-wacom-0.20.0.tar.bz2 from [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/input-wacom/](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/input-wacom/) (2013-12-06)
     Now this is where thing went wrong.. It may seem stupid (and maybe it was..)

     When you open the above link you will notice this: Looking for the latest version? Download xf86-input-wacom-0.22.1.tar.bz2 (546.6 kB)

     This is NOT what you want! ..and it was what I downloaded ..and it was the reason it didn't work! May seem stupid but I downloaded the WRONG file!!
     All because I saw that "latest version" warning. You want **input-wacom-0.20.0.tar.bz2**

.2: Unpack the tar.bz2 to your desktop (or wherever) You will get a folder named "**input-wacom-0.20.0**"

.3: Now you must open terminal in that folder directory.
     To do that I folowed this little thing from [http://satyadeepk.in/2011/02/quicktip-right-click-to-open-terminal-in-current-directory-in-ubuntu/](http://satyadeepk.in/2011/02/quicktip-right-click-to-open-terminal-in-current-directory-in-ubuntu/)
     from this cool guy Satyadeep Karnati. Thank you Satyadeep!

     Open terminal (Ctrl+Alt+T) and paste:

[B]     sudo apt-get install nautilus-open-terminal
[/B]
     and then:[B]

     killall nautilus && nautilus

[/B]     Close that terminal window.
     Now you can open any folder in terminal by right clicking a chose "open in terminal". Do that in your "**input-wacom-0.20.0**" folder.
     You may need to open a folder through the launcher because your desktop content will vanish temporarily. Don't worry.. it's all there.

.4: Now open a text editor and paste the following:

**./configure**
**sudo cp ./<kernel version>/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet**
**sudo cp ./<kernel version>/wacom_w8001.ko /lib/modules/`uname -r`/kernel/drivers/input/touchscreen**
[B]sudo depmod -a

[/B]     You have to replace **<kernel version>** by **3.7** in the 2nd and 3rd lines (I think this is correct for all recent Ubuntu systems).
     Now open a new terminal (don't close the current) and paste **`uname -r`**. Copy the result and replace **`uname -r` **in the 2nd and 3rd lines.
     Close that terminal. (not the first one)

     In my case it looks like this:

**./configure**
**sudo cp ./3.7/wacom.ko /lib/modules/3.11.0-19-generic/kernel/drivers/input/tablet**
**sudo cp ./3.7/wacom_w8001.ko /lib/modules/3.11.0-19-generic/kernel/drivers/input/touchscreen**
**sudo depmod -a**

.5: Now in the terminal you opened earlier in the "**input-wacom-0.20.0**" folder directory, paste it.. one line each time..

.6: Reboot!

.7: **Have a blast!!**




Any questions.. just ask!
I know how you're feeling!

---

### Post by pdc on 2014-03-23
I am delighted it is all working for you; I would love there to be a clearer write somewhere for everyone about wacom; so I find the documentation confusing and contradictory

thanks for describing how you installed [COLOR="#008000"][B]input-wacom
[/B][/COLOR]

the page for it


says > The input-wacom driver is a set of loadable kernel modules [COLOR="#EE82EE"]which allows new tablets[/COLOR] to be used with systems using [COLOR="#EE82EE"]kernels as old as Linux 2.6.30[/COLOR].  ...but you are using 3.11.0-19-generic 

the next line says > Because of this, we recommend upgrading your kernel if possible [COLOR="#EE82EE"]and only installing this driver when absolutely necessary[/COLOR]. .........so strange to me if you have a pretty recent kernel ...

I see you say the template is

> sudo cp ./<kernel version>/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet

and then you did 

> sudo cp ./3.7/wacom.ko /lib/modules/3.11.0-19-generic/kernel/drivers/input/tablet

.............because I would have thought the phrase > [COLOR="#0000FF"]<kernel version>[/COLOR] applies to  your kernel version, which I see as > [COLOR="#800080"]3.11.0-19-generic[/COLOR] so I would have thought the command might have been 

> sudo cp ./3.11.0-19-generic/wacom.ko /lib/modules/3.11.0-19-generic/kernel/drivers/input/tablet


so I am a bit puzzled but delighted you are enjoying your wacom tablet

---

### Post by Ricardo_Raimundo on 2014-03-28
> **pdc said:**
> but you are using 3.11.0-19-generic. so strange to me if you have a pretty recent kernel ...

I'm nor sure I understand what you mean.. The most recent the kernel is, the better.. I think..

> **pdc said:**
> [COLOR=#000000]so I would have thought the command might have been [/COLOR]

[COLOR=#000000]*sudo cp ./3.11.0-19-generic/wacom.ko /lib/modules/3.11.0-19-generic/kernel/drivers/input/tablet*[/COLOR]

Yes.. that a little (a lot!) confusing. 3.7 is a folder inside the input-wacom folder. That "cp" makes Ubuntu copy that 3.7 folder to the destination drivers folder.
3.7 is what you want to copy if you have a recent kernel.

---

### Post by Nugar on 2014-07-26
I'm curious about this. I have the CTH-480 Small, did all this steps and it sort of works. I get the pen functionality, but not the eraser or the pressure.

Also, it works the same on Windows 8.1 as a guest with Linux Mint 17 as a host. 

Are you getting the whole functions?

---

### Post by Ricardo_Raimundo on 2014-07-26
Hi there Nugar!

Yep.. all is running as it should.

Which did you downloaded? 0.22.0 or 0.22.1?
Try downloading the other one (the one you didn't download) and repeat the process.

The eraser is not a big deal (at least for me.. I never use it) but no pressure sensitivity is a pain!

If this doesn't solve your question try contacting the guys at the [COLOR=#555555][FONT=sans-serif]linuxwacom-discuss [/FONT][/COLOR]mailing list (the 3rd option) here: [http://sourceforge.net/p/linuxwacom/mailman/?source=navbar](http://sourceforge.net/p/linuxwacom/mailman/?source=navbar) and ask them for help.

They are very nice people and I'm sure someone will come to the rescue.
My knowledge is very limited and without the good people at linux wacom I would not have made it!

Good luck!
Let me know how it went..

---

### Post by Nugar on 2014-07-26
Hola Ricardo,

I downloaded 0.22.1.

I found a couple of threads elsewhere that allowed me to actually have a profile and save to it. And the pressure does work, at least on the configuration applet, but I haven't been able to use that pressure on Photoshop under virtualbox, for example.

While writing this post, I noticed that the pressure actually works in Krita, which is nice.

Cheers,

---

### Post by Ricardo_Raimundo on 2014-07-26
Hola!

So, I guess virtualbox is not translating the pressure settings correctly.
Try downloading Gimp and check if it works. I think you have to turn pressure in Gimp settings. But if it works in Krita, I guess it's working fine.

Cheers! Happy "penning"! ;)

---

### Post by Nugar on 2014-07-26
Hola again,

Yes, I just googled and The GIMP does work, even the eraser. :)

Now I just need to develop a workflow for RAW files under Linux.

Thanks!

---

### Post by Ricardo_Raimundo on 2014-07-26
Raw you say.. I see..

Take a look :shock: at this: [http://www.darktable.org/](http://www.darktable.org/)

---

### Post by Nugar on 2014-07-26
Thanks :)

---

