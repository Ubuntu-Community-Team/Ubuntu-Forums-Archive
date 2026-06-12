---
title: "can't see the GUI &amp; Text mode"
date: 2009-07-05
forum: Hardware
---

### Post by YanY on 2009-07-05
[LEFT][FONT=Times New Roman][SIZE=4]Hi[/SIZE][/FONT][/LEFT]
 
[LEFT][FONT=Times New Roman][SIZE=4]i post it n the General Help[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]but... i didn't got any real A[/SIZE][/FONT][/LEFT]
 
 
[LEFT][FONT=Times New Roman][SIZE=4]I'm new to Ubunto[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Don't know much :/[/SIZE][/FONT][/LEFT]
 
 
[LEFT][FONT=Times New Roman][SIZE=4]I installed the Ubuntu desktop 9.4 on a P3 computer[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]And it work fine, for a P3...[/SIZE][/FONT][/LEFT]
 
 
[LEFT][FONT=Times New Roman][SIZE=4]I had a one problem with the screen resolution,[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Ubuntu don't recognize the screen and give me only 800x600 resolution.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]It worked like that about a week without shutting down.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]I don't remember what did I do but now I can't see the GUI and the Text mode (ctrl+alt+f1).[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]I accessed with SSH [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Stop the GDM and start it + restart the machine[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]but it didn't help.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]I removed the GDM from the startup with RCCONF,[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Restart the machine and I success to load the Text mode.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]When I start the GDM again I couldn't see the GUI and i have lost the Text mode too.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]Slpci show me that the system recognize the video card.[/SIZE][/FONT][/LEFT]
 
 
[LEFT][FONT=Times New Roman][SIZE=4]1) what can I do to fix the GDM loading problem ?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]2) how can i fix the resolution ? or check if the video card support resolution over 800x600[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=4]the motherboar is ASUS CUSI-m[/SIZE][/FONT][/LEFT]
 
[LEFT][FONT=Times New Roman][SIZE=4]the Ubuntu find the Hardware [/SIZE][/FONT]
[SIZE=4][FONT=Times New Roman]it's all on board.[/FONT][/SIZE]
[SIZE=4][FONT=Times New Roman]i worked with the desktop GUI for a week [/FONT][/SIZE]
[SIZE=4][FONT=Times New Roman]and i want to get it back even the 800x600[/FONT][/SIZE]
[FONT=Times New Roman]:neutral:[/FONT][/LEFT]
 
[LEFT][FONT=Times New Roman][SIZE=4]it will be easier for me to fix the resolution ander GUI[/SIZE][/FONT][/LEFT]
 
 
 
 
 
[LEFT][FONT=Times New Roman][SIZE=4]Thanks for advanced[/SIZE][/FONT][/LEFT]

---

### Post by kilowattradio on 2009-07-05
Hi, Please post the make and model of your video card on that computer here so others can help. If you can get back in terminal mode try using the command *startx* as **root** and a print out of what is happening will appear on the screen. Save the output to a file and post it here so someone call tell you what the problem is.
To access your root account in Ubuntu use:
```

polk@polk-desktop$ sudo su -
Password: *********
root@polk-desktop:~# passwd
Enter new UNIX password: ******
Retype new UNIX password: *****

```
Now at anytime you can log in as root in a terminal or from an account using 
```
su -
```

---

### Post by YanY on 2009-07-05
[FONT=Arial][SIZE=4]thanks for the reply.[/SIZE][/FONT]
[FONT=Arial][SIZE=4][/SIZE][/FONT] 
[FONT=Arial][SIZE=4]this the manual[/SIZE][/FONT]
[http://www.unitycorp.co.jp/support/download/manual/370/cusi_m_e.pdf](http://www.unitycorp.co.jp/support/download/manual/370/cusi_m_e.pdf)
[FONT=Arial][SIZE=4][/SIZE][/FONT] 
[FONT=Arial][SIZE=4]and this is the chipset[/SIZE][/FONT]
[http://en.wikipedia.org/wiki/SiS_630/730](http://en.wikipedia.org/wiki/SiS_630/730)
 
[COLOR=red]Resolution Up to 1920x1200 8bpp/16bpp 60 Hz[/COLOR]
[COLOR=#ff0000][/COLOR] 
[FONT=Arial][SIZE=4][COLOR=black]i fuond a drivers[/COLOR][/SIZE][/FONT]
[http://driverscollection.com/?H=CUSI-M&By=ASUS&SS=Linux](http://driverscollection.com/?H=CUSI-M&By=ASUS&SS=Linux)
[FONT=Arial][SIZE=4][COLOR=black]but...  yes, i don't know which 1 of the 2 linux i need to download and..  i don't know who to install drivers :([/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=4][/SIZE][/FONT] 
"you can get back in terminal mode try using the command *startx* as **root** and a print out of what is happening will appear on the screen"
 
[FONT=Arial][SIZE=4]again.. [/SIZE][/FONT]
[FONT=Arial][SIZE=4]i don't know how  to do it [/SIZE][/FONT]
[FONT=Arial][SIZE=4]can you tel me the commands?[/SIZE][/FONT]
[FONT=Arial][SIZE=4]i can access by ssh as root.[/SIZE][/FONT]
[FONT=Arial][SIZE=4][/SIZE][/FONT] 
[FONT=Arial][SIZE=4]thanks again :)[/SIZE][/FONT]

---

