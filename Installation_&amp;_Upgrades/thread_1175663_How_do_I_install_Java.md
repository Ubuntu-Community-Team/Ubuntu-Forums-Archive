---
title: "How do I install Java?"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by Ubuter on 2009-06-01
Hi,
I need help Installing *Java* on my **Ubuntu 9.04**. I'm not that new to **Ubuntu**, but I still can't get *Java* working. What [COLOR=DarkOrange]Version[/COLOR] do I download and how do I install it?:(
_Please Help_,
***Ubuter***

---

### Post by Therion on 2009-06-01
Quickest way, in my opinion, is to simply open a terminal and type in (Cut and Paste):```
sudo apt-get install ubuntu-restricted-extras
```Follow the prompts, agree to the EULA's etc., and you're good to go.

---

### Post by Ubuter on 2009-06-01
How do I know It's installed?
I did as you said but this> online recording program ([Here]("http://www.screentoaster.com/record")) does not work. it freezes on "loading java applet".
HELP AGAIN,
Ubuter

---

### Post by oldos2er on 2009-06-01
You may need to install sun-java6-plugin as well:
```
sudo apt-get install sun-java6-plugin
```

---

### Post by gordintoronto on 2009-06-01
I went to Cool Math Games, clicked on "Java games," picked the first one, and Firefox said, "you need to install more stuff, click here to install it."  Worked like a charm.

With my previous Ubuntu installation, I muddied the waters by installing some stuff which was not from Sun.  Never did get Cool Math Games working.


> **Ubuter said:**
> How do I know It's installed?
I did as you said but this> online recording program ([Here]("http://www.screentoaster.com/record")) does not work. it freezes on "loading java applet".
HELP AGAIN,
Ubuter

---

### Post by Ubuter on 2009-06-03
[SIZE=6][SIZE=4]Well, i went to cool math games
and went to the classic java games section. clicked a random game. Firefox said plugins are needed. clicked that and 3 pligins were listed:[/SIZE]
[/SIZE]> The icedtea web browser plugin
the java(tm) plug-in, Java se 6
The java(tm) plug-in, Java se 5.0[SIZE=4]when I clicked next, I had to type in my pass, which i did. then it loaded and said an error occured.
[/SIZE] [SIZE=6][SIZE=4]It said:[/SIZE]
[/SIZE]> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[SIZE=6][SIZE=4]it was the same for the rest of the plugins. HEEEEEEEEEELP![/SIZE]:([/SIZE]

---

### Post by Therion on 2009-06-03
Open a Terminal and type in (just cut and paste) the following:```
sudo dpkg --configure -a
```
and follow the prompts if you get any.

---

### Post by dragos_iliescu_2005 on 2009-06-03
> **Ubuter said:**
> [SIZE=6][SIZE=4]Well, i went to cool math games
and went to the classic java games section. clicked a random game. Firefox said plugins are needed. clicked that and 3 pligins were listed:[/SIZE]
[/SIZE][SIZE=4]when I clicked next, I had to type in my pass, which i did. then it loaded and said an error occured.
[/SIZE] [SIZE=6][SIZE=4]It said:[/SIZE]
[/SIZE][SIZE=6][SIZE=4]it was the same for the rest of the plugins. HEEEEEEEEEELP![/SIZE]:([/SIZE]

Open Synaptic, make a search for 'sun-java'; rigth-click and select to reinstall all packages related to sun-java.
For firefox to 'have' java, just install 'sun-java-plugin'

---

### Post by indianinside on 2009-06-03
You can see some documentation here 

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Ubuter on 2009-06-03
> **Therion said:**
> Open a Terminal and type in (just cut and paste) the following:```
sudo dpkg --configure -a
```and follow the prompts if you get any.
[SIZE=5]I did what therion said, and click install for the updates again. they all installed, but when i restarted firefox it said plugins needed clicked and the same were there. click install for the icedtea and when it loaded is said already installed, same 4 the rest. But the game still does not work. do I like need to resart my computer or what? HEEEEEEEEEEEEEEEEEEEEEELP!
[/SIZE]

---

### Post by Ubuter on 2009-06-03
[FONT=Impact][SIZE=6][COLOR=Red]:KSnever mind, its working now!
Java games for me! :-)
[/COLOR][/SIZE][/FONT]

---

