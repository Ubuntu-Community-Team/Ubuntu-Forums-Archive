---
title: "installing java on xubuntu 9.04 on ps3"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by suprc4 on 2009-08-26
Hi I am running xubuntu 9.04 on my ps3. I'm trying to install java but it doesnt work i tried the 64 bit and regular one. I have the files saved to my desktop, should I put it somewhere else or is it o here? Anyway I go to my desktop location in the terminal and i type chmod a+x jre-6u15-linux-i586.bin  then i type ./jre-6u15-linux-i586.bin  and it shows the user agreement and i just go all the way down and i type yes and this is what it shows
Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
Extracting...
./install.sfx.26901: 1: Syntax error: "(" unexpected
Failed to extract the files.  Please refer to the Troubleshooting section of
the Installation Instructions on the download page for more information.


When i try the 64 bit version it shows this

Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
Extracting...
./install.sfx.26565: 1: ELF: not found
./install.sfx.26565: 2: Syntax error: ")" unexpected


Can someone please help me!!! Thank You.

---

### Post by tenghoward on 2009-08-26
> **suprc4 said:**
> Hi I am running xubuntu 9.04 on my ps3. I'm trying to install java but it doesnt work i tried the 64 bit and regular one. I have the files saved to my desktop, should I put it somewhere else or is it o here? Anyway I go to my desktop location in the terminal and i type chmod a+x jre-6u15-linux-i586.bin  then i type ./jre-6u15-linux-i586.bin  and it shows the user agreement and i just go all the way down and i type yes and this is what it shows
Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
Extracting...
./install.sfx.26901: 1: Syntax error: "(" unexpected
Failed to extract the files.  Please refer to the Troubleshooting section of
the Installation Instructions on the download page for more information.


When i try the 64 bit version it shows this

Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
Extracting...
./install.sfx.26565: 1: ELF: not found
./install.sfx.26565: 2: Syntax error: ")" unexpected


Can someone please help me!!! Thank You.

PS3's CPU is using PPC as its architecture. Meaning that both i586 and x64 version of Java cannot run on you PS3.

Instead, install icedtea-gcjwebplugin. (If it is available in repos, offers Java support on firefox)

---

### Post by suprc4 on 2009-08-26
So there is no way to install java on it? I just want to play runescape and all those funorb games thats y i installed xubuntu on my ps3. Is their anyway i can play those or is their a different version of java I have to get?

---

### Post by tenghoward on 2009-08-26
> **suprc4 said:**
> So there is no way to install java on it? I just want to play runescape and all those funorb games thats y i installed xubuntu on my ps3. Is their anyway i can play those or is their a different version of java I have to get?

Try to find and install icedtea-gcjwebplugin. It is open source alternative to Java.

It should allows you to play RuneScape on Firefox.

---

### Post by LowSky on 2009-08-26
the PS3 uses a different type of computer processor, think old school iMacs that couldn't run MS Windows, while the new one can.

you need the icedtea, it is installable under synaptic.

---

### Post by suprc4 on 2009-08-26
Thanks so much for helping me I can finally play runescape on my ps3!!!!! I installed that icedtea thing and it works perfectly fine oh thank you soo much.!!!!!

---

### Post by suprc4 on 2009-08-27
Well the thing is I can play runescape but its like really super slow. And i cant play it on opera. Anything i can do to increase performance to make runescape run better so i can get a more enjoyable playing time? Also when i check my java version it says [B]Your Java version is 1.6.0_0      [FONT=Verdana]

and it says to update to version 6 update 14. it shows on my first post that ive tried that already. is their anyway where i can update this icedtea thing so it can make my java the latest version. That will hopefully make runescape run faster. And can someone please give tips on how to make my ubuntu faster. Thank You.
[/FONT][/B]

---

