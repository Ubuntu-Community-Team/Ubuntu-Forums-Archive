---
title: "Can MSoft fonts install in 8.04.1"
date: 2008-08-06
forum: General Help
---

### Post by willieboy on 2008-08-06
Is it possible to install the MSoft TTF fonts in Ubuntu 8.04.1. ?
there is one in particular I would like to have, it's the Arial TTF font.
As you can probably tell from this, I'm new to Linux.
I've looked at all the Ubuntu fonts but none are as good as Arial.


Thanks.

---

### Post by OutOfReach on 2008-08-06
Actually, yes you can install those, goto the terminal (Applications>Accessories>Terminal) and type in the following:
```
sudo apt-get install msttcorefonts
```

Hope this help.

---

### Post by willieboy on 2008-08-08
&#9474; msttcorefonts uses defoma  
 &#9474;                                                          
 &#9474; Msttcorefonts uses the DEbian FOnt MAnager (defoma). If you wish to use   
 &#9474; the fonts provided by this package under the X Window System, you must    
 &#9474; configure it to use defoma fonts.                                      
 &#9474;                                                                       
 &#9474; The easiest way to do so is to use the x-ttcidfont-conf package. For      
 &#9474; more information, install the x-ttcidfont-conf package and consult its   
 &#9474; documentation under /usr/share/doc/x-ttcidfont-conf.                      
 &#9474;                                                                           
 &#9474; For uses of msttcorefonts not related to the X Window System (e.g.      
 &#9474; printing) this is not required.   

----------------------------------------------------------------------------------------
I tried that but I get th3 message above, I don't think I'd like to try that as I don't know enough about Linux.

However, I was in System / Appearance and into Fonts.

In details / Help/ Adding a True type font, it states :-
Click on Details.
Click on "Go to Font folder". The fonts Folder opens.
Open a file manager and select the font that you want to add
to the fonts folder.

There is no "Go to Font Folder" to click on.

I really only want to install the MSoft Arial font, if I can get it to install I'll maybe install a few more.

I have the MSoft fonts in a folder "Fonts" on the desktop.

---

### Post by damoxc on 2008-08-08
try installing the package the message suggested, see if that resolves things.
```
sudo apt-get install x-ttcidfont-conf
sudo apt-get install msttfcorefonts
```

alternatively ```
sudo apt-get install ubuntu-restricted-extras
``` also installs them and many other things you may need.

---

### Post by willieboy on 2008-08-08
Reading package lists... Done
Building dependency tree       
Reading state information... Done
x-ttcidfont-conf is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

----------------------------------------------------------
I installed :-
sudo apt-get install x-ttcidfont-conf
but I got the message above.

Then I tried the 
sudo apt-get install msttfcorefonts
it went OK

I tried again :-
sudo apt-get install x-ttcidfont-conf
but I got the same message above.

I used your 3rd link
"sudo apt-get install ubuntu-restricted-extras"
 but when the install was finished I again got  the message to install 
 "sudo apt-get install x-ttcidfont-conf"

Seems some good things in that link, many thanks.

---

### Post by Vorian Grey on 2008-08-08
I backup all my Windows fonts because I don't want to have to hunt all over the internet to find them again. All I do is open Nautilus and do Fonts:/// in the address bar and copy the fonts from my backup to the fonts folder.

---

### Post by willieboy on 2008-08-09
I think I've not given to the correct information, I realise after I spent a few hours last evening with the fonts and not getting them to work. I tried all the suggestions above, and I got 3 packages of MS FF fonts that installed OK, or so the program stated.

I was trying to get TT fonts to work in all applications in Ubuntu, firefox etc etc.

I believe TT fonts can only be used in Programs installed in Linux that use them in windows, Office for example. I got Crossover and it installs the fonts OK.
To narrow it all dowm, is it possible to get Arial TT to work in FireFox, I doubt it, but if you don't ask you never find out.

Thanks to all you good guys for your help.

---

### Post by steveneddy on 2008-08-09
Open up your /home folder

hit the 

CTRL+H keys to show hidden folders

scroll down until you see the 

.fonts folder

copy your fonts there that you would like to use.

Then in terminal, copy and paste this then hit enter

```

fc-cache -fv

```

and you can use your new font.

**Sometimes** you need to restart to get all new fonts to work correctly.

---

### Post by steveneddy on 2008-08-09
You are welcome.

If this solved it for you, please mark the thread as solved.

:D

---

### Post by willieboy on 2008-08-09
Many thanks for your help.

---

