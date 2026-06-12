---
title: "crossover MS office fonts problems"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by ctejos on 2009-03-19
I've just installed MS Office 2007 on my PC using CrossOver but I cannot see any text (in Word, Excel, etc.) because it appears entirely aliased. My bet is that I have fonts problems.

Does anyone now how to solve this problem?

Cheers

CT

---

### Post by kestrel1 on 2009-03-19
Have you got the msttcorefonts installed?

---

### Post by ctejos on 2009-03-19
Thanks K. for your suggestion, it seams I had not installed the msttcorefonts since when I did

sudo apt-get install msttcorefonts

I started downloading a lot of fonts.

Unfortunately now I have 2 problems, because the msttcorefonts failed and send this message

dpkg: error processing g15daemon (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of g15macro:
 g15macro depends on g15daemon; however:
  Package g15daemon is not configured yet.

....and I still cannot see MS office texts....

Any ideas?

Cheers,

CT

---

### Post by kestrel1 on 2009-03-19
Try typing```
sudo dpkg -a --configure
```
in a terminal & try to install the fonts again or just install the Ubuntu-restricted-extras instead as the msttcorefonts are part of it.

---

### Post by ctejos on 2009-03-19
Hi K. this is pehaps my bad day...

When I proceeded with 

sudo dpkg -a --configure

or

sudo apt-get install ubuntu-restricted-extras

or

sudo apt-get install msttcorefonts


I got exactly the same error message:

"dpkg: error processing g15daemon (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of g15macro:
 g15macro depends on g15daemon; however:
  Package g15daemon is not configured yet.
dpkg: error processing g15macro (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 g15daemon
 g15macro
"

Any ideas?

CT

---

### Post by kestrel1 on 2009-03-19
Do you happen to have a Logitech G15 keyboard?
If so it appears to be related to that. Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=267118&page=44](http://ubuntuforums.org/showthread.php?t=267118&page=44)

---

### Post by ctejos on 2009-03-19
unfortunatelly not, I don't have a logitech G15 keybord, so I'm not sure it has something to do with what is reported in that thread....

---

### Post by kestrel1 on 2009-03-19
Go to synaptic & see if the G15daemon is installed. If you do not have a Logitech G11 or G15 keyboard I can see no reason for it to be installed.

---

### Post by ctejos on 2009-03-19
I removed g15deamon and g15macro, so now I don't have the second problem any more. I did install msttcorefonts and ubuntu-restricted-extras, but I still have the original problem, I cannot read anything from MS office

Ideas?

CT

---

### Post by kestrel1 on 2009-03-19
Can you post a screen shot of the problem.
Do you have Desktop Effects enabled? If so disable them & see if the problem is still there. You may want to restart X server to check this. To restart X logout or press CTRL, ALT & Backspace. You will need to log back in either way.
Also go to System -> Preferences -> Appearance & under the Fonts tab check that you have Subpixel Smoothing (LCD's) checked.

---

### Post by ctejos on 2009-03-20
I had already checked th options subpixel smoothing and no Desktop effects, so that's unfortunately not the problem.

I'm posting a png screenshot to show you the problem

CT

---

### Post by ctejos on 2009-03-20
Hi K., I've got another clue to solve this mystery. Apparently it's not a font problem but might be a rendering problem. I just zoomed in (up to 150%) and everything looked perfect, but below 140% everything starts to mess up.

Ideas?

---

### Post by kestrel1 on 2009-03-20
What graphics card do you have?

---

### Post by ctejos on 2009-03-20
GForce4 MX 4000

---

### Post by kestrel1 on 2009-03-20
Similar to mine. I will have a look when I get to the machine.

---

### Post by kestrel1 on 2009-03-20
Have a look at this link: [http://ubuntuforums.org/showthread.php?p=6667437#post6667437](http://ubuntuforums.org/showthread.php?p=6667437#post6667437) 
The suggestion in there helped me with a similar problem, related to wine.

---

### Post by dcabrera01 on 2009-04-23
find at the \home directory\.cxoffice the file user.reg. Open the file and append the next two lines at the end.

[Software\\Wine\\X11 Driver] 1232814138
"ClientSideWithRender"="N"

Hope it helps.

---

