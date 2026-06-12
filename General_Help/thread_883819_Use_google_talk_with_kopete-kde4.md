---
title: "Use google talk with kopete-kde4"
date: 2008-08-08
forum: General Help
---

### Post by patrickaupperle on 2008-08-08
I have the kde 4.1 repo. I installed kubuntu-kde4-desktop. All went well. I have a perfect kde 4.1 desktop. Only problem is kopete won't work with my google talk account. I have been searching for about an hour and a half and have found no answers. When I try to connect I get this message:
```
SSL support could not be initialized for account ***************@gmail.com. This is most likely because the QCA TLS plugin is not installed on your system.
```
in a popup. 
Ok, so I installed qca-tls and still got the same message. I really do not know where to go from here. Please help.

---

### Post by patrickaupperle on 2008-08-08
BUMP Please Help!

---

### Post by patrickaupperle on 2008-08-08
bump!

---

### Post by Ayuthia on 2008-08-08
> **patrickaupperle said:**
> I have the kde 4.1 repo. I installed kubuntu-kde4-desktop. All went well. I have a perfect kde 4.1 desktop. Only problem is kopete won't work with my google talk account. I have been searching for about an hour and a half and have found no answers. When I try to connect I get this message:
```
SSL support could not be initialized for account ***************@gmail.com. This is most likely because the QCA TLS plugin is not installed on your system.
```
in a popup. 
Ok, so I installed qca-tls and still got the same message. I really do not know where to go from here. Please help.

Are you using port 5223 instead of 5222?  If you don't know what I am talking about, go to Settings->Configure and select your gmail id and Modify Account.  Go to the Connection tab and make sure that the Overrid default server information is checked, the Server is talk.google.com, and the Port is set to 5223.

Hope that helps.

---

### Post by patrickaupperle on 2008-08-09
> **Ayuthia said:**
> Are you using port 5223 instead of 5222?  If you don't know what I am talking about, go to Settings->Configure and select your gmail id and Modify Account.  Go to the Connection tab and make sure that the Overrid default server information is checked, the Server is talk.google.com, and the Port is set to 5223.

Hope that helps.

I am pretty sure it is right.

Yes, I am in gnome right now, same result either way though. I originally found the problem in kde 4. Pidgin works fine, but I really don't like it as well.

---

### Post by netboy541 on 2008-08-10
this is a problem all the way across the board with kopete. it has nothing to do with kde 3 or 4, as I am running KDE 3.5.9.   I recently upgraded to Hardy, and now I cannot connect to Google Talk with kopete, so you're not crazy, at least not in this sense. :)

Straight off the kopete.kde.org website: 


Jabber SSL support stopped working, I get the message that the QCA TLS plugin is probably missing. What am I supposed to do?

As the error message indicates, you are missing the QCA TLS plugin, which handles the Jabber plugin's TLS/SSL encryption. Install the package qca-tls (and eventually qca-ossl) or retrieve the plugin from [http://delta.affinix.com/qca](http://delta.affinix.com/qca). Please note that you only need to install the qca-tls plugin, _not_ the QCA library itself. A recompilation of Kopete is not necessary, in fact not even a restart. In case you have installed the plugin and it still won't work, Qt can probably not find it. Since qca-tls installs itself as a Qt plugin, you will have to make sure that it gets installed to the plugin directory of the Qt version you are using to run Kopete.




Now, what makes me irritable, is I installed this plugin, and now I get a error saying the jabber server doesn't support the operation.

I've attached a screengrab of that....

My settings are exactly the same as my feisty box, talk.google.com, all boxes checked, port 5223, and it connects without any problems... 


Anyone get this to work out there or have we uncovered a <gasp> bug?

---

### Post by Speed Demon on 2008-08-10
Mine works perfect using this fix... a box will pop up about certificate for gmail.com not being verified just click do not show again and then continue... VOILA perfectly working GTALK... Tested using Kubuntu Hardy KDE 4.1

```
sudo apt-get install qca-tls libqca2-plugin-ossl
```

PS set the google talk port to 5223 and enable SSL

---

### Post by netboy541 on 2008-08-10
nope.

> rminick@nomachine1:~$ sudo apt-get install qca-tls libqca2-plugin-ossl
Reading package lists... Done
Building dependency tree
Reading state information... Done
qca-tls is already the newest version.
libqca2-plugin-ossl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rminick@nomachine1:~$


running 

Linux nomachine1 2.6.24-19-server #1 SMP Sat Jul 12 00:40:01 UTC 2008 i686 GNU/Linux
Hardy
and kopete 0.12.7

---

### Post by netboy541 on 2008-08-10
Got it.  Change the port from 5223 to 443.

It connected. yaaaaaaaaaaaaaaaay!

EDIT :  OK, so I thought that worked.  It connected once, but won't connect again.  hmm...

well, i switched it back to 5223 and it worked.

beats the devil out of me.

thanks tho for reading....

---

### Post by Speed Demon on 2008-08-11
Err...update yo Kopete... i tested on
Kopete
Version 0.50.80
Using KDE 4.1.00 (KDE 4.1.0)

otherwise... yeah i meant to say put it on 5223 and ssl... on connect it wont verify certificate for gmail.com tell it do not show again and continue and it will work... I hope.

---

### Post by piousp on 2008-08-12
Indeed, you need to install the QCA TLS plugin.

---

### Post by emanaton on 2008-11-06
> **Speed Demon said:**
> ```
sudo apt-get install qca-tls libqca2-plugin-ossl
```

This turned out to be the solution for me on a fresh install of the new 8.10 release. Thanks Speed Demon!

Sean P. O. MacCath-Moran
[www.emanaton.com](www.emanaton.com)

---

### Post by camahuetos on 2009-01-03
Well, I just installed Kubuntu Intrepid Ibex (8.10) and got a problem like this: "There was an error of autentication with the server: Fail to access for an unknown problem".

I tried all the possible solutions here and none of them works for me, not even changing the port from 5223 to 443 (I also installed QCA and OSSL without succes).

Can anyone suggest me some answer?

---

### Post by schmy on 2009-01-18
I, too, am looking for answers now. 
I have tried many variations of "talk" and no "talk", "gmail.com" over "google.com", ports 5222, 5223, 443, SSL and no SSL, overrides, reinstalls, updating plugins...

For the record:

Intrepid (8.10) with KDE 4.1. All updates installed. MSN working fine.

Did I miss anything?

As a side note, the Gmail chat page and the Google Talk page appear to have removed the how-tos for other clients. (I'm sure they used to have a Jabber How-to but I can't seem to find it).

Another aside: I tried using Pidgin to connect to Gmail chat. Similar issues. I didn't bother testing for long because it soon crashed.

Thanks in advance, people!

---

### Post by noworry on 2009-02-20
I am also unable to connect to gtalk using kde 4.2 kopete 0.70.0 !!!

Raised a bug - [https://bugs.kde.org/show_bug.cgi?id=185072](https://bugs.kde.org/show_bug.cgi?id=185072)

---

### Post by rameshvr on 2010-03-13
oops. I am still stuck with Kopete+GTalk.
Even my qca-tls and libqca2-plugin-ossl are latest.
I tried changing port to both 5223 and 443. 

No way.
Help please..

---

