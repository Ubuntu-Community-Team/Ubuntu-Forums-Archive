---
title: "headphones do not mute speakers"
date: 2010-03-27
forum: Hardware
---

### Post by marort on 2010-03-27
Every time I connect my headphones to my ASUS K50 Notebook, speakers do not mute.

Apparently this is a known issue in Ubuntu 9.10. I have navigated through the web in search for a solution without positive results yet. Do you know if there is a fix for this problem already?

Thanks.

---

### Post by Yvan300 on 2010-03-27
Wow, i wished this happened to me in some situations. It would be a god send!

---

### Post by djdg on 2011-07-07
I have this problem too. Have been searching for a loooong time.

---

### Post by lidex on 2011-07-07
> **marort said:**
> Every time I connect my headphones to my ASUS K50 Notebook, speakers do not mute.

Apparently this is a known issue in Ubuntu 9.10. I have navigated through the web in search for a solution without positive results yet. Do you know if there is a fix for this problem already?

Thanks.

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by gordintoronto on 2011-07-08
Or you could install 11.04, where it is almost certainly fixed.

---

### Post by Yellow Pasque on 2011-07-08
> **gordintoronto said:**
> Or you could install 11.04, where it is almost certainly fixed.
Unfortunately, that's not the case. Even with the latest Ubuntu and/or ALSA, jack sensing is still problematic and often requires the 'model=' trick. That's a design flaw with Intel's High Definition Azalia standard, which is very flexible in allowing OEM's to customize things, but then isn't much of a standard. ;)

---

### Post by spanky1023 on 2011-11-11
> **gordintoronto said:**
> Or you could install 11.04, where it is almost certainly fixed.

11.10 64 bit installed here, and the same problem.  
anyone have a fix ?

never had an issue with 10.04 ?  Win7 works fine as well ?

---

### Post by gordintoronto on 2011-11-11
Tell us about your computer? When you start Sound Settings and click the Hardware tab, what shows up?

---

### Post by northd_tech on 2011-11-11
The output of these terminal commands might be informative (as well as from lidex's script in post #4 above):

```
sudo lshw -C multimedia
lsmod | grep snd
```

---

### Post by starrtennis on 2012-06-15
> **gordintoronto said:**
> Or you could install 11.04, where it is almost certainly fixed.

You could politely ask the Ubuntu development team to fix a known issue that seems to be rampant and largely unsolved. Or you could install a new operating system. Your choice n.n

---

