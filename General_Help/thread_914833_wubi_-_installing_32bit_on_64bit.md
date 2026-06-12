---
title: "wubi - installing 32bit on 64bit"
date: 2008-09-09
forum: General Help
---

### Post by joey-elijah on 2008-09-09
I use Vista 64bit - and i used to have Ubuntu 64 bit installed but after "issues" deleted it totally and installed ubuntu via Wubi... which was also 64 bit! >_<

is there anyway to get 32bit ubuntu installed and not 64 bit? I don't need the hassles of 64bit for what i'm doing atm with linux - which is reviews, testing, learning to dev etc

howdy yohah!

---

### Post by Kumagoro on 2008-09-09
Start wubi with --32bit argument (eg from command line)

---

### Post by joey-elijah on 2008-09-09
in windows? or in wubi? or wuni in cmd? or 0_o

---

### Post by tuxxy on 2008-09-09
> I use Vista 64bit - and i used to have Ubuntu 64 bit installed but after "issues" deleted it totally and installed ubuntu via Wub

It would take some real serious problems for me to downgrade to a 32-bit OS, could these not be fixed, what exactly were the issues you had with?

---

### Post by Kumagoro on 2008-09-09
> **joey-elijah said:**
> in windows? or in wubi? or wuni in cmd? or 0_o

The wubi installer file under windows...

Just type in command line wubi --32bit (ofc. being in wubi folder)

---

### Post by joey-elijah on 2008-09-09
> **tuxxy said:**
> It would take some real serious problems for me to downgrade to a 32-bit OS, could these not be fixed, what exactly were the issues you had with?

not much really, i managed to get flash working etc but several applications i wanted to review just wouldn't install in 64bit environment.

also, several hardware pieces wouldn't install/work/be forced to work under 64bit... there's numerous agonizing posts regarding it all to be found around here somewhere!

main reason is for adobe air which is still in alpha for linux, for only for 32bit.. no matter how much i tried fooling it into thinking it was on 32bit, it just wouldn't install.

i use 64 bit windows vista and haven't had much problems at all. annoyingly, i was about to switch to Ubuntu from a dual boot to a single boot with xp in a virtual box for photoshop etc, but apart from lack of adobe air (petty huh) the whole system was glitchy, slow and not as fast as 32bit had been on same hardware... 

(amd 64 x2 6000+ @ 3.0ghz, 4gb 667mhz ram, nvidia 8500gt 1gb....)

---

### Post by nemomarlin on 2009-02-26
I use Wubi 32 bit too. Flash just works in 32 bit. Flash is just really borderline dysfunctional in 64 bit.

---

### Post by Gobbenobber on 2009-07-09
Just wanted to tell, that if you (like me) dont understand how you start wubi with --32bit argument, you can make a shortcut to "Wubi.exe" and right click that, then in destination type "--32bit" after the destination and then also write "--32bit" in Comments

---

### Post by xfatherjack on 2010-11-02
> **Gobbenobber said:**
> Just wanted to tell, that if you (like me) dont understand how you start wubi with --32bit argument, you can make a shortcut to "Wubi.exe" and right click that, then in destination type "--32bit" after the destination and then also write "--32bit" in Comments

Over a year since you wrote this 'stuff' "dont understand how you start wubi with --32bit argument", neither do I.
I'm in a similar boat to you now and I can not find improved information. It still does not make any sense to a 'lay-person/non-Geek' like me.
I know what 'Terminal' is, a list of commands and SIMPLE instructions would have been nice. 
I will have to Install from a CD + Format HD etc. etc. 
Geniuses write all this software, they still cannot communicate with average-2-DUD IQ people, Pity, What a CROCK.

---

### Post by themoonlaughs on 2011-05-19
...this works with 11.04!

*from the Ubuntu Wiki ([https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)*)
**Can I force Wubi to download and install a 32 bit version of Ubuntu?**

 Yes: either [pre-download the appropriate 32 bit ISO manually]("https://wiki.ubuntu.com/WubiGuide#ManuallyDownloadISO") and place it in the same folder as Wubi.exe or start Wubi with the "--32bit" argument. 
To  modify arguments, right-click Wubi.exe and select "Create Shortcut".  Then right-click the shortcut, select Properties, and modify the Target  line, for example: "C:\Documents and  Settings\<user>\Desktop\wubi.exe" --32bit

---

### Post by cajuuh on 2011-09-21
yeap! Don't work... Keep receiving the compability error..

---

### Post by DirtyPC on 2012-02-25
For people who are getting stuck with this, clearing up those ends. Terminal is Command prompt (for windows)

you need to put terminal in the folder of wubi.exe.

for me its in my downloads folder, so in command prompt, it looks like this for me:

cd /Users/homeuser/Downloads

wubi --32bit

Do this in Command console. Obviously replace homeuser with your name..

(cd is change directory)

---

