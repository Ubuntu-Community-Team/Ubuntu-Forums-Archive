---
title: "install Firefox 3.0.3 ??"
date: 2008-09-28
forum: General Help
---

### Post by ra2008 on 2008-09-28
Hi,,

what are the commands or procedure to install [_firefox 3.0.3_]("http://www.mozilla-europe.org/en/firefox/"). i downloaded the file and it is a source file. i tried simple commands like  **./configure** or **make** but dont work.
any hints??
thanks

---

### Post by p_quarles on 2008-09-28
It's not a source file, it's a binary. To run it, either invoke the full path:
```
/home/`whoami`/firefox/firefox-bin
```
Or add the location of the binary to the path.

---

### Post by ra2008 on 2008-09-28
> **p_quarles said:**
> It's not a source file, it's a binary. To run it, either invoke the full path:
```
/home/`whoami`/firefox/firefox-bin
```
Or add the location of the binary to the path.

hi,
 i found the file firefox-bin inside.
and when i i type the above command i get: 
```
/home/raed/firefox/firefox-bin: error while loading shared libraries: libjemalloc.so: cannot open shared object file: No such file or directory

```

and if cd to /home/username/firefox and type:
firefox-bin
i get: 
raed@raed-laptop:~/firefox$ firefox-bin
bash: firefox-bin: command not found
????

---

### Post by ra2008 on 2008-10-02
how to update Firefox using Synaptics.
because whenever i try to loggin to my hotmail account it says that i have to update to firefox 3.0.3.

hints????

---

### Post by Ryadt on 2008-10-02
What version of ubuntu are you using?

---

### Post by ra2008 on 2008-10-02
> **ryadt said:**
> what version of ubuntu are you using?

8.04

---

### Post by Ryadt on 2008-10-02
> **ra2008 said:**
> 8.04
If so, then firefox 3.0.3 should be the version you are using. Double check it in Help > About Mozilla Firefox.

---

### Post by ra2008 on 2008-10-02
> **Ryadt said:**
> If so, then firefox 3.0.3 should be the version you are using. Double check it in Help > About Mozilla Firefox.
hi u r right ,
but why hotmail asks me for update. [ATTACH]87053[/ATTACH]
\???

---

### Post by Ryadt on 2008-10-02
Maybe they want you to use Internet Explorer. Who knows? ;)

---

### Post by ccy on 2008-10-02
Did u guys try to type about: in the address and hit enter? My FF says version 1.9.0.3 in this way, although from Help -> About Mozilla Firefox, it says version 3.0.3.

---

### Post by Paul41 on 2008-10-02
> **ra2008 said:**
> hi u r right ,
but why hotmail asks me for update. [ATTACH]87053[/ATTACH]
\???

I have seen other people on here with the same problem. It seems to be a hotmail issue.

---

### Post by Joeb454 on 2008-10-02
Perhaps installing the User-Agent Switcher plugin for firefox would help

---

### Post by laurenl on 2008-10-02
I have installed the FF 3.0.3 but sometimes i would get an creash report error then FF is not working properly. Why is that so can anyone help me...

---

### Post by Paul41 on 2008-10-03
> **laurenl said:**
> I have installed the FF 3.0.3 but sometimes i would get an creash report error then FF is not working properly. Why is that so can anyone help me...

This is a different problem than the original topic so I would suggest searching the forum to see if other people have had the same problem and if not start a new thread with the information from your crash report. I think you will be more likely to get help with your specific problem that way.

---

### Post by ra2008 on 2008-10-03
> **ccy said:**
> Did u guys try to type about: in the address and hit enter? My FF says version 1.9.0.3 in this way, although from Help -> About Mozilla Firefox, it says version 3.0.3.
hi.
i tried and here it is what i get:

**Build identifier: Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.3**

---

### Post by ccy on 2008-10-03
> **ra2008 said:**
> hi.
i tried and here it is what i get:

**Build identifier: Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.3**

Attached is my result. Have no idea why this could happen.

---

### Post by ra2008 on 2008-10-03
> **Joeb454 said:**
> Perhaps installing the User-Agent Switcher plugin for firefox would help

sorry it didnt help

---

### Post by Ogar93 on 2008-10-03
type in terminal

firefox --version

---

### Post by Diablo713 on 2008-10-03
My firefox version is 2.0.0.6 how can i install the new one,i am using ubuntu version 7.10.

---

### Post by tspan on 2008-10-03
> **ccy said:**
> Attached is my result. Have no idea why this could happen.
It happens to me too. "1.9.0.3" string seems to be hard-coded to Firefox. Go to "about:" and click on "View -> Page Source". You should see a line: 
```
<p id="version">&about.version; 1.9.0.3</p>
```
I don't think it should cause any problem.

---

### Post by XxLeekxX on 2008-10-04
I went to another thread ([http://ubuntuforums.org/showthread.php?p=5857692](http://ubuntuforums.org/showthread.php?p=5857692))  and they solved through this method.

The only thing I did different was remove the value "Ubuntu" from the general.useragent.vendor string

---

### Post by Sef on 2008-10-04
> Did u guys try to type about: in the address and hit enter? My FF says version 1.9.0.3 in this way, although from Help -> About Mozilla Firefox, it says version 3.0.3.

3.0.3 is the Firefox version.

1.9.0.3 is the Gecko version.  Gecko is the back end of Firefox.  It is used on a number of browsers.

---

### Post by frankleeee on 2008-10-04
> **Diablo713 said:**
> My firefox version is 2.0.0.6 how can i install the new one,i am using ubuntu version 7.10.

This will instruct you how to do it.
[http://ubuntuzilla.wiki.sourceforge.net/#updatefirefox](http://ubuntuzilla.wiki.sourceforge.net/#updatefirefox)

---

### Post by ra2008 on 2008-10-04
> **Diablo713 said:**
> My firefox version is 2.0.0.6 how can i install the new one,i am using ubuntu version 7.10.

use synaptics

---

### Post by ra2008 on 2008-10-04
> **XxLeekxX said:**
> I went to another thread ([http://ubuntuforums.org/showthread.php?p=5857692](http://ubuntuforums.org/showthread.php?p=5857692))  and they solved through this method.

The only thing I did different was remove the value "Ubuntu" from the general.useragent.vendor string

it works, i removed the vendor "Ubuntu" form "general.useragent.vendor"

---

