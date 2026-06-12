---
title: "Unable to install core azureus version 4.2.0.2 -- keep getting prompted to install it"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by natifnatal34 on 2009-04-14
I am very new to Linux and Ubuntu.   I actually installed Ubuntu 8.10  this past Easter weekend on a Toshiba laptop.   I am in love already and only wish I had done this a long time ago.

In any case, I have Vuze 3.1.1.0 currently installed.   I keep getting prompted to install Core Azureus Version 4.2.0.2.   After clicking the Update button, I get the following.

Downloading: [[],]
Downloading: [[],]
    Downloading: [[http://torrents.aelitis.com:88/torrents/Azureus4.2.0.2.jar.torrent:](http://torrents.aelitis.com:88/torrents/Azureus4.2.0.2.jar.torrent:) torrent]
      Downloading: [http://torrents.aelitis.com:88/torrents/Azureus4.2.0.2.jar.torrent:](http://torrents.aelitis.com:88/torrents/Azureus4.2.0.2.jar.torrent:) torrent
        Downloading: [http://torrents.aelitis.com:88/torrents/Azureus4.2.0.2.jar.torrent](http://torrents.aelitis.com:88/torrents/Azureus4.2.0.2.jar.torrent)
      Downloading: Azureus4.2.0.2.jar
Torrent download complete
Data verified successfully

Afterwards, I click the Restart button.  The application does get restarted, but I get prompted again to install Core Azureus Version 4.2.0.2 - and of course Vuze 3.1.1.0 is still there.

Any help, would be much appreciated -- including how to remove Azureus 3.1.1.0 completely (if that would help solve the problem)

Thanks in advance

---

### Post by cackles on 2009-04-24
I've reinstalled azureus about ... I dunno actually, at least 30 times in the past few days, on third total rebuild for today just now.

I ended up just telling it to install, reboot later then goto tools -> options and expand interface then untick auto update etc.

It has installed fine all 3 times today and a few times last night, maybe fixed?

---

### Post by johnsdagg on 2009-04-25
i have the same problem - installed a fresh installation of ubuntu 9.04 on a blank hard drive, installed azureus and vuze 3.1.1.0 using package manager. upon getting into azureus, i was prompted to upgrade to azureus version 4.2.0.2. which i did. 
 
now, every time i start azureus it wants to reinstall the version 4.2.0.2 update. every time.
 
 
on a side note: like other people have written, ubuntu 9.04 installer destroyed grub on my other hard drive that lives in the same box. i reinstalled it in a terminal, disconnected that drive and then reinstalled 9.04 on the other blank drive. when done i reconnected the first drive and it's fine - i have a dual boot situation in which i choose boot drive in my mobo bios. works just fine.

---

### Post by Thiras on 2009-04-27
Same problem on Jaunty

---

### Post by SpyORG on 2009-04-28
Just as **cackles** said, try uncheck an option 'Automatically open the Update Assistant when an update is available' under Tools->Options->Interface->Start.

AFAIR, there were no such problem with updates in previous versions of Vuze.

---

### Post by kiridude on 2009-04-28
have you guys tried deluge?

It's a very lightweight program that takes care of all my torrent needs very well. It is also open source.

I used to use Vuze but felt it had way too much unnecessary baggage.


Cackles, like your sig :)

---

### Post by shatterblast on 2009-04-28
May I suggest trying Deluge instead of Azureus?

---

### Post by 1993cb7 on 2009-06-03
i think im going to give Deluge a try since i use VUZE on Vista to sync videos and such but i have no use for anything fancy on Linux.

I keep getting the same problem when i open it.

I downloaded Vuze 4.0 from their website and ran one of the files as an executable and it opened Vuze 4.0 but i don't think it installed it and im not sure how to install from a tar.gz

---

### Post by &lt;iostream&gt; on 2009-06-06
I am having the very same problem when it wants to update to a newer version, but never seems to install the file. It seems to be using a .jar file type. Is ubuntu compatible with this file type?

---

### Post by anbuchelvansci on 2009-06-18
*[SIZE=3][COLOR=Red]Just Google Search the below Link then Download And Double Click it will Work Fine for me.[/COLOR][/SIZE]*

[SIZE=3][COLOR=SeaGreen]**vuze_4.2.0.2-1~getdeb1_i386.deb**[/COLOR][/SIZE]


                                                                                                              [SIZE=6][COLOR=DarkRed]**OR**[/COLOR][/SIZE]
[COLOR=Purple]
[/COLOR][CENTER][FONT=Arial Black][SIZE=3][I][COLOR=Purple]http://apt.ubuntu-tw.org/getdeb/ubuntu
/jaunty/vu/[/COLOR][/I][/SIZE][/FONT]

[SIZE=6][COLOR=DarkRed][B]OR
[/B][/COLOR][/SIZE] [http://85.114.135.53/ubuntu/jaunty/vu/vuze_4.2.0.2-1~getdeb1_i386.deb]("http://85.114.135.53/ubuntu/jaunty/vu/vuze_4.2.0.2-1%7Egetdeb1_i386.deb")


[LEFT]                                                      Kindly Help Anyone . Spread Your Knowladge


[/LEFT]



[/CENTER]

---

### Post by anbuchelvansci on 2009-06-18
[SIZE=4][/SIZE][B]
JUST CLICK AND ENJOY

[/B][http://85.114.135.53/ubuntu/jaunty/vu/vuze_4.2.0.2-1~getdeb1_i386.deb]("http://85.114.135.53/ubuntu/jaunty/vu/vuze_4.2.0.2-1%7Egetdeb1_i386.deb")

                                                                   --Spread Knowladge

---

### Post by openam on 2009-06-25
Here might be a solution [http://www.azureuswiki.com/index.php/Failed_Update](http://www.azureuswiki.com/index.php/Failed_Update) I actually ran the install from getdeb.net, but it said that I still don't have rights to update.  It looks like it might be the solution.

---

### Post by stuart221 on 2009-10-17
Try this [http://ubuntuforums.org/showthread.php?t=1228361&highlight=vuze](http://ubuntuforums.org/showthread.php?t=1228361&highlight=vuze)

---

### Post by couzin2000 on 2009-10-19
Even with the new version this will cause great problems. The 4.2 installed version tells me that "/usr/share/vuze/" is not open to write access under my username.

SOLUTION:
[LIST]
[*]If it is open, go to the Vuze program, go into "File > Exit";
[*]open a terminal;
[*]type ```
sudo nautilus
```
[*]navigate to the [FONT="Courier New"]/usr/share/[/FONT] folder;
[*]select the [FONT="Courier New"]vuze[/FONT] folder and right click to get the Properties dialog;
[*]go to the Permissions tab;
[*]go into "Group" and set the group name to your username, the set access to "Create and Delete files";
[*]close the window and the terminal;
[*]restart Vuze.
[/LIST]

You should not encounter problems updating Vuze after this.
Enjoy!

---

