---
title: "How to adjust brightness on hp laptops in Gutsy"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by olavjunior on 2008-01-21
Thanks to Mike Lopez for making this litle script [http://tech.mikelopez.info/2007/10/27/lcd-brightness-keys-not-working-in-kubuntu-gutsy/#comment-112929]("http://tech.mikelopez.info/2007/10/27/lcd-brightness-keys-not-working-in-kubuntu-gutsy/#comment-112929") :popcorn:

Here's how to:
Download the attached lcdbryt.sh

Run this from where you downloaded it to:
   1. sudo cp lcdbryt.sh /usr/bin
   2. sudo chmod +x /usr/bin/lcdbryt.sh
   3. sudo gedit /etc/acpi/video_brightnessup.sh
         1. add the following line at the end of the file
            lcdbryt.sh up
         2. save (Ctrl+s alt+F4)
   4. sudo gedit /etc/acpi/video_brightnessdown.sh
         1. add the following line at the end of the file
            lcdbryt.sh dn
         2. save (Ctrl+s alt+F4)


This should be it, now at least my Fn F6 & F7 works perfectly!

This also works great in Hardy! Enjoy

---

### Post by tehsnipes on 2008-01-21
can anyone confirm this??

---

### Post by olavjunior on 2008-01-22
I can confirm that it worked perfectly on my hp dv2130

---

### Post by rufensis on 2008-01-22
This worked perfectly on an HP Pavilion dv2000 laptop, too.

---

### Post by Z_o-s-o on 2008-01-22
The DV2000's arent supported out of the box?

The keyboard controls on my Dv6215 worked like a charm out of the box.

---

### Post by olavjunior on 2008-01-22
No, mine worked somewhat under Feisty, meaning it just went bright or dimmed. But didn't work at all under Gutsy (until now)

---

### Post by rosegarden78 on 2008-01-22
You can hack a work-around by adjusting gamma correction which fixed my brightness problem on an overly-bright standard LCD display 1024x768 laptop at 86 ppi.

Make two shell scripts gc-up and gc-dn with a text editor in your /home directory

nano gc-up
#!/bin/sh
#gamma up
xgamma -gamma 1.0

nano gc-dn
#!/bin/sh
#gamma down
xgamma -gamma 0.75

chmod +x gc-up
chmod +x gc-dn

The commands above make the files executable.  You can also do all this from the GUI with the right click.  Finally add the scripts to keyboard shortcuts but you'll need to use Ctrl-F7 and Ctrl-F8 if the function key isn't detected in settings.  Just type under command:

bash /home/gc-up
bash /home/gc-dn

And don't forget to set your key combination.

---

### Post by tehsnipes on 2008-01-22
thanks mates, it works like a charm

---

### Post by olavjunior on 2008-01-23
I tried adjusting the gamma, but that didn't give the right effect for me. The colors just got darker or something, not the backlight. The easy way to use gamma is ```
xgamma gamma 1.0 (or smaller..)
``` if you want to try

---

### Post by tehsnipes on 2008-01-24
Sticky this map, highly helpful and easy and should easily solve the problems for us noobs out here.

thanks so much man.

---

### Post by chowdy on 2008-01-27
Awesome!! Thanks a lot!

---

### Post by camini on 2008-02-15
Thanks!  I had been waiting for this for months!!
It works perfectly on my HP dv2000 (dv2386ea).

---

### Post by muddyh2o on 2008-03-10
that did the trick on my HP 8710w running gutsy.  thanks!

---

### Post by adamfussing on 2008-04-13
thanks a lot.. worked like a charm :)

---

### Post by drpaul on 2008-04-13
Seeing this thread made me experiment. On an hp dv6150us, gutsy seems to control screen brightness and audio controls across the top right out of the box.

I never expected it, but ....

Who'ld a thunk it!

Paul

---

### Post by olavjunior on 2008-04-18
Does anyone know how Hardy is doing on our hps?

---

### Post by chriswyatt on 2008-04-22
Screen brightness is not working on my DV2058ea although worked in a previous beta :( .  Is it worth using this script on Hardy Heron?  Screen brightness didn't work on Gutsy either, annoyingly I've only just found this script.

---

### Post by chriswyatt on 2008-04-22
Yes, installed this script and it works a treat.  Thankyou :popcorn:

Gets a bit confused when switching between AC and battery mode, I expected this might be the case and it's a minor issue :) .

---

### Post by olavjunior on 2008-04-23
ok. I'm on Hardy but only upgraded, so I guess my script is still working

---

### Post by tom56 on 2008-04-27
> **chriswyatt said:**
> Screen brightness is not working on my DV2058ea although worked in a previous beta :( .  Is it worth using this script on Hardy Heron?  Screen brightness didn't work on Gutsy either, annoyingly I've only just found this script.

Yeah I have this too. Brightness control doesn't work on my dv2315nr in Hardy (final), though it worked in the beta. Wonder what broke it?

Hibernate doesn't work either, though suspend does.

Everything else works out of the box :) (including webcam and mic!)

---

### Post by qhaz on 2008-04-28
This works on my HP Pavilion dv2000 running Hardy.
Thanks!

---

### Post by miglo on 2008-05-02
This did NOT work on a Dell m1330.

---

### Post by HunkieChan on 2008-05-02
works great for me..!! thanks alot

---

### Post by mempman on 2008-05-04
Thanks man~!


> **olavjunior said:**
> Thanks to Mike Lopez for making this litle script [http://tech.mikelopez.info/2007/10/27/lcd-brightness-keys-not-working-in-kubuntu-gutsy/#comment-112929]("http://tech.mikelopez.info/2007/10/27/lcd-brightness-keys-not-working-in-kubuntu-gutsy/#comment-112929") :popcorn:

Here's how to:
Download the attached lcdbryt.sh

Run this from where you downloaded it to:
   1. sudo cp lcdbryt.sh /usr/bin
   2. sudo chmod +x /usr/bin/lcdbryt.sh
   3. sudo gedit /etc/acpi/video_brightnessup.sh
         1. add the following line at the end of the file
            lcdbryt.sh up
         2. save (Ctrl+s alt+F4)
   4. sudo gedit /etc/acpi/video_brightnessdown.sh
         1. add the following line at the end of the file
            lcdbryt.sh dn
         2. save (Ctrl+s alt+F4)


This should be it, now at least my Fn F6 & F7 works perfectly!

This also works great in Hardy! Enjoy

---

### Post by microwaver on 2008-05-04
Did everything from Step 1 till end, didn't work the tiniest bit.

---

### Post by misterioso on 2008-05-11
david@bentolila:~$ lcdbryt.sh up
cat: /proc/acpi/video/VGA/LCD/brightness: Arquivo ou diretório inexistente
/usr/bin/lcdbryt.sh: line 18: [: 1: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 2: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 3: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 4: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 5: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 6: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 7: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 8: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 9: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 10: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 11: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 12: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 13: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 14: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 15: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 16: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 17: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 18: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 19: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 20: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 21: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 22: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 23: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 24: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 25: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 26: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 27: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 28: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 29: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 30: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 31: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 32: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 33: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 34: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 35: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 36: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 37: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 38: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 39: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 40: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 41: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 42: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 43: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 44: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 45: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 46: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 47: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 48: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 49: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 50: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 51: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 52: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 53: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 54: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 55: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 56: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 57: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 58: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 59: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 60: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 61: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 62: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 63: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 64: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 65: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 66: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 67: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 68: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 69: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 70: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 71: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 72: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 73: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 74: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 75: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 76: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 77: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 78: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 79: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 80: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 81: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 82: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 83: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 84: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 85: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 86: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 87: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 88: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 89: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 90: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 91: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 92: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 93: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 94: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 95: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 96: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 97: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 98: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 99: operador unário esperado
/usr/bin/lcdbryt.sh: line 18: [: 100: operador unário esperado

/usr/bin/lcdbryt.sh: line 38: /proc/acpi/video/VGA/LCD/brightness: Arquivo ou diretório inexistente


HP DV 2000

in beta brightness was OK.. in final bug :( 

my ubuntu ins in portuguese... so 
*operador unário esperado = unit operator expected 

*Arquivo ou diretório inexistente = file or directory not found

some help???


root@bentolila:/proc/acpi# ls
ac_adapter  button               event  info            sleep
alarm       dsdt                 fadt   power_resource  thermal_zone
battery     embedded_controller  fan    processor       wakeup

+++++++++++++++++++++++++++++++++++++++++
I confirm, it's work!!!!!
but i have to reinstall ubuntu to crate a file brightness!!!!
thkx

---

### Post by deleyd on 2008-05-12
On my HPdv9410us, tried this lcdbryt.sh thing. F7/F8 keys didn't change brightness. Then tried replacing video_brightnessup.sh & down.sh at:

[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/145337/comments/81](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/145337/comments/81)

F7/F8 keys still didn't do anything. 

But then I tried at a terminal prompt just entering:
lcdbryt.sh up
and that worked! Repeating that a few times got my screen nice and bright.

(I also noticed a discrepancy between the lcdbryt.sh script I downloaded and the one posted at 

[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/145337/comments/35](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/145337/comments/35)

the one posted there has a # in front of both
#acpi_fakekey
whereas the one I downloaded does not. (And I'm so new to Linux I don't even know what that # means.)

---

### Post by holnrew on 2008-05-14
I tried this on an advent 8212 and tried another method I found on the forum and neither have worked. All the other function keys work, so this is very frustrating. And the screen is constantly dim. Is there a simple way to just increase the brightness?

---

### Post by holnrew on 2008-05-14
I've found the brightness applet so never mind.

Should I undo the changes somehow because it didn't work?

---

### Post by andreselsuave on 2008-05-18
Not working at all on my hp 8710p :( any other solutions?

---

### Post by drdanield@gmail.com on 2008-06-08
> **olavjunior said:**
> Thanks to Mike Lopez for making this litle script [http://tech.mikelopez.info/2007/10/27/lcd-brightness-keys-not-working-in-kubuntu-gutsy/#comment-112929]("http://tech.mikelopez.info/2007/10/27/lcd-brightness-keys-not-working-in-kubuntu-gutsy/#comment-112929") :popcorn:

Here's how to:
Download the attached lcdbryt.sh

Run this from where you downloaded it to:
   1. sudo cp lcdbryt.sh /usr/bin
   2. sudo chmod +x /usr/bin/lcdbryt.sh
   3. sudo gedit /etc/acpi/video_brightnessup.sh
         1. add the following line at the end of the file
            lcdbryt.sh up
         2. save (Ctrl+s alt+F4)
   4. sudo gedit /etc/acpi/video_brightnessdown.sh
         1. add the following line at the end of the file
            lcdbryt.sh dn
         2. save (Ctrl+s alt+F4)




This works to for function keys on Gateway M-6319, but it doesn't fix the brightness applet on the panel.

---

### Post by drdanield@gmail.com on 2008-06-08
Gateway M-6319 has similar problem. Brightness doesn't work by either function keys nor brightness applet.  The function keys work following similar "hacks" on /etc/apci/video_brightnessup.sh and video_brightnessdown.sh as described on following forum threads:
[http://ubuntuforums.org/showthread.php?t=767374](http://ubuntuforums.org/showthread.php?t=767374)
[http://ubuntuforums.org/showthread.php?t=673946](http://ubuntuforums.org/showthread.php?t=673946)
[http://ubuntuforums.org/showthread.php?t=767219](http://ubuntuforums.org/showthread.php?t=767219)

But applet still doesn't work. I think whatever is called by acpi_fakekey 224 and 225 is not working correctly.
<code>
$ sudo dmidecode -s system-manufacturer
Gateway
$ sudo dmidecode -s system-version
3409361R
$ sudo dmidecode -s system-product-name
M-6319
</code>
xev output for function keys brightness up (key code 212) and down (101):
<code>
  KeyPress event, serial 30, synthetic NO, window 0x3400001,
    root 0x59, subw 0x0, time 2511327, (731,745), root:(736,796),
    state 0x0, keycode 212 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False
  
  KeyRelease event, serial 30, synthetic NO, window 0x3400001,
    root 0x59, subw 0x0, time 2511327, (731,745), root:(736,796),
    state 0x0, keycode 212 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
  
  KeyPress event, serial 30, synthetic NO, window 0x3400001,
    root 0x59, subw 0x0, time 2513724, (731,745), root:(736,796),
    state 0x0, keycode 101 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False
  
  KeyRelease event, serial 30, synthetic NO, window 0x3400001,
    root 0x59, subw 0x0, time 2513724, (731,745), root:(736,796),
    state 0x0, keycode 101 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
</code>


I would really appreciate it if this can be fixed fundamentally by an update from main Ubutnu repository.  It's an important problem for laptops running on battery.

---

### Post by stefgro on 2008-06-10
Does not work on HP nx6325 and Hardy.

---

### Post by davidryderuk on 2008-06-11
This works on a Hi-grade VA250D laptop in Hardy. I second this problem being fixed in the hardy alphas and betas but not in the final version of hardy or in gutsy. It is also not common to all distributions as the brightness control works in other distributions such as mandriva (can't remember which others but there are a few).

Thanks for the fix.

---

### Post by Mitch_Arsenal on 2008-06-28
This works on a hp dv2224ea running Hardy. Thanks

---

### Post by tonolau on 2008-07-02
thanks

my laptop is hp v3334.

succeed.

---

