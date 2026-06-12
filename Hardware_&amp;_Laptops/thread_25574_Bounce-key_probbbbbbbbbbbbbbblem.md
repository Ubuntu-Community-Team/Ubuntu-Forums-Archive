---
title: "Bounce-key probbbbbbbbbbbbbbblem"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by arrizaba on 2005-04-10
After I upgraded to Hoary I find a bounce-key problem, i.e. everytime I try to type something, once in a while I get a letter repeating like crazyyyyyyyyyyyyyyyyyyyyyyyyy.
I had the same thing with kernel 2.4 and 2.6.4 but the problem was related to the Synaptics Touchpad driver not properly loaded in those versions. I knew how to fix this from the link [COLOR=Blue]http://www.marcsaric.de/m30_linux1.html[/COLOR].

I did not have this problem when I installed Warty; the Synaptics was properly dealt with and I found no bounce-key problem. This was properly due to a later version of the kernel 2.6.8-5. 

But, after I upgraded to Hoary, the bounce-key problem appeared again!! 
And, now the Synaptics Touchpad is properly configured, so i do not know what is causing the problem....  ](*,) 

Does someone know a solution??? This bbbbbbbbbbbbbbbbbbbbbbbounce-key problem is driving me mad...

---

### Post by alastair on 2005-04-10
I've seen weird key problems like this with an odd USB/hub keyboard setup. I would have thought it was a keyboard issue? What type of keyboard?

---

### Post by risager on 2005-04-10
I have the same problem on my Toshiba, but I do not know how to solve it. I might try using psmouse driver instead of synaptics driver. That way the fix on the site you linked to might work. But I will not have all the nice synaptics stuff like scrolling etc.

---

### Post by arrizaba on 2005-04-11
Hi,

Well, I also have a Toshiba. It might actually be a problem related to toshibas only. 
I've seen some other solution posted in a different forum ([COLOR=Blue]http://zzrough.free.fr/toshiba-m30.php[/COLOR]), which had to do with enabling the bounce-keys in the accesibility menu of the keyboard: System -> Preferences -> Keyboard -> Accesibility, and adjust the value to 5 ms. 
This solution did not work for me however.

---

### Post by risager on 2005-04-11
What sort of worked for me is disabling Repeat keys. But this is not a very pleasant solution. I want to be able to use repeat keys. Especially for deleting. And there still seem to be random delays between actual typing and screen outputs. The problem occours whenever you accidentally touch the touch-pad while typing.

---

### Post by arrizaba on 2005-04-11
Yes, turning off Repat Keys is a bit too drastic.
I also find the delays between typing and output on the screen. 
But, the problems occur also when I am not touching the Synaptics Touchpad.

I have found a possible solution (which I should test as soon as I get home to my ubuntu computer), which is to disable the xkb and add a xmodmap for your keyboard. This is what I found:

>  I prefer a disabled Xkb-extension together with a private modmap,
since I was not satisfied by the accessX-solutions (after the keyboard
bug disapeared the key repetition was strange). But it was quite easy to
start X with Xkb-extension (in my case for a German keyboard), do a
short xmodmap -pke >/tmp/xmodmap.xkb, leave X as soon as possible (the
keyboard bug can be very annoying ;-) afterwards. You can then replace
the Xkb stuff in XF86Config-4 by
Option "XkbDisable" "true"
and put the xmodmap at a position, where your xinitrc will automatically
load it (/etc/X11/Xmodmap in my case, running Debian Woody). 

If you use a US-international keyboard layout, this should be pretty straightforward. I'll test it later and then post the results.

---

### Post by dusu on 2005-04-11
If this can cheer you up, I also suffer from this problem, but only from time to time !!
I also have a Toshiba laptop  :-?
Now for me, it's not only the keys that are repeated, but everything goes like the speed of light :
the waiting icon in firefox turns like hell, the banner in xmms is unreadable is unreadable because it's so fast.
I would be happy if my 933MHz Celeron was also turning at 3GHz  :grin: ! But that's not the case :(

As I said, for me it happens from time to time, and I just have to reboot the computer to make it go away.

Is it always like this for you ?

---

### Post by risager on 2005-04-11
I now solved the bounce-key situation on my Toshiba. In the file /etc/modules I replaced the line
```
psmouse
``` 
with
```
psmouse rate=40
``` 
as described in the original post. Previously I had just removed the module with 'rmmod psmouse' and then done 'modprobe psmouse rate=40'. That didn't work. But after rebooting with the new '/etc/modules' file the bouncings and occasional delays are completely gone.  :grin: 

Hope it works also for the rest of you Toshiba users.

---

### Post by arrizaba on 2005-04-20
It does! Thnx Risager.

---

