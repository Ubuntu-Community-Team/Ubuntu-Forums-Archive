---
title: "CUPS and Canon MG 4200"
date: 2017-10-28
forum: Hardware
---

### Post by LeXav on 2017-10-28
Hi !

On a fresh 17.10 ubuntu, I've an issue with my Canon MG 4200.

There are two printers on my network : a HP laserjet and a canon MG. Both are installed easily. Jobs are sent to the printers : fine.

But, on the canon all the prints are shifted to the bottom. The bottom of the page is never printed. I thought the page set-up was wrong. But, no : it's right (A4) 

I checked the ppd files of the both printers. I spotted that the imageablearea is different.

On the HP : 

```
*ImageableArea A4/A4: "11.34 11.34 583.66 830.66"
```

On the canon : 

```
*ImageableArea A4: "18.141732283465 106.015748031496 577.133858267717 819.212598425197"
```

I edited the canon's file ( sudo nano and save ). But CUPS need to be restarted to set in this new file. And then .... CUPS replace the wrong ppd file again.
How can I stop CUPS to replace ppd files a each start ? 

Thanks a lot ! :)

( A sorry for my bad english... #typicalfrench)

---

### Post by pdc on 2017-10-28
Bonjour LeXav; bienvenue; 

there could be several drivers to work the 4200: there could be open-source Gutenprint; Canon drivers; and since 17.04, Ubuntu has airprint support; and your printer is airprint-compatible; 

so I guess if you go to PRINTERS folder; IMPRIMANTES? ..... and right-click on the only icon?? for your MG ...... look in MAKE & MODEL ......... drag the window to the right to see all the text ....... what does it say?

If you want to try the Canon drivers that they supply, go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100466802.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100466802.html) and click to download and SAVE what will be [COLOR="#0000FF"]cnijfilter-mg4200series-3.80-1-deb.tar.gz[/COLOR]

open a terminal; copy the commands below one by one; paste into the terminal and hit the ENTER key ..

```
cd Downloads
```

```
tar -zxvf cnijfilter-mg4200series-3.80-1-deb.tar.gz
```

```
cd cnijfilter-mg4200series-3.80-1-deb
```

```
./install.sh
```      and that final command runs the install script and may ask you a couple of questions: you can name it what you want: perhaps something that makes clear it is Canon Drivers

_____________________________

Tradition has been that **installed** ppds are in /etc/cups/ppd. The *database* is in /usr/share/ppd. ............ so to edit one would need ```
cd /etc/cups/ppd
``` and perhaps the ```
ls
``` command to list what is there; and then gksudo gedit MG4200-series.ppd or whatever the ppd is called, to edit it ........... where are your ppd files stored?

---

### Post by LeXav on 2017-10-29
Hi !

I did what you've explain to me and it's work perfectly fine ! 
Merci beaucoup ! ;)

---

### Post by pdc on 2017-10-29
très bon!

---

