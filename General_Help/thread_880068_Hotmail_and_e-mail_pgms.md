---
title: "Hotmail and e-mail pgms"
date: 2008-08-04
forum: General Help
---

### Post by dragonlord2598 on 2008-08-04
I can't get any of ubuntu's e-mail programs to retrieve hotmail.

---

### Post by ibuclaw on 2008-08-04
Hotmail is a pop client, is it not?

There is a, albeit slightly old, howto here:
[http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)

Follow it and see where you get.

Regards
Iain

---

### Post by Jdm111 on 2008-08-04
Hotmail is webmail

---

### Post by dragonlord2598 on 2008-08-04
> **tinivole said:**
> Hotmail is a pop client, is it not?

There is a, albeit slightly old, howto here:
[http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)

Follow it and see where you get.

Regards
Iain

It wont accept my password

---

### Post by northern lights on 2008-08-04
Hotmail is a heap of crap. It doesn't even work with M$ Outlook out of the box (see [here]("http://support.microsoft.com/kb/287424")).

You have to install some secondary app, which is, I suppose, the case just so that it won't run with any other mail client.

Get a gmail account and life will be easier.
Need an invite, send a PM.

[EDIT]While it might still work (honestly, haven't read the whole thing, too tired - ready for bed), lemme bring to your attention that the guide is from Summer 2006...)[/EDIT]

---

### Post by geeth on 2008-08-04
Hotmail made changes a few years back that it's accounts that haven't been up for a long time, or have't been accessed by a email client would not be able to have this accss for free.

I haven't read the message for over a year, but from what I remember. You have to have a account - or something to that effect - to be able to access hotmail through a client.

They did this around the time the spam filtering they use pretty much stopped working :p

IMO go gmail

---

### Post by robotman5 on 2008-08-04
yoy could always get a Sympatico Email (you can use it to login on msn messneger to!):guitar:

---

### Post by solitaire on 2008-08-04
Thunderbird with the "Web Mail" plugins work for me! (pick up Hotmail / Yahoo and Google mail...

---

### Post by geeth on 2008-08-04
> **solitaire said:**
> Thunderbird with the "Web Mail" plugins work for me! (pick up Hotmail / Yahoo and Google mail...

How old is your hotmail account though?

When I setup a new account a few years back, it didn't matter what client I used, I just got the same message.
Things may have changed since I tried though :p

---

### Post by solitaire on 2008-08-04
my hotmail is VERY old!!
I got it over 8 years ago! :P

---

### Post by geeth on 2008-08-04
> **solitaire said:**
> my hotmail is VERY old!!
I got it over 8 years ago! :P

LoL
Thats what I thought. Make a new random one and try to set it up. I can't atm as I'm at work but I don't think that you could.

---

### Post by solitaire on 2008-08-04
Have you got Web mail and Hotmail Web mail plugin's for Thunderbird?


*Update*
created a new @hotmail.co.uk account
sent test messages to account using my normal default account
stuck details in to thunderbird
Stuck in password when asked
downloaded test messages. 
no problems!!

:D:D

---

### Post by geeth on 2008-08-04
And now we know!

---

### Post by dragonlord2598 on 2008-08-06
I installed all of the pug-ins (I think) it still dont work

HELP

---

### Post by solitaire on 2008-08-06
OK

Start "ThunderBird" go to "Edit" then "Account Settings"
Click on "Add Account"
Select "Web Mail", click "Next"
enter in your name and your hotmail address click "Next"
enter your hotmail address and click "Next"
Then click "Finish"

In "Thunderbird" then go to "Tools" / "Add-ons"
select "WebMail" and click on "Preferences"

In the "Servers" tab "POP" & "SMTP" should be "Running"
ports:
POP : 1100
SMTP: 2500
Make sure "Enable at startup" is ticked for both of these.

IMAP should be "Stopped" .

Click "Close"

Go to "WebMail - Hotmail" and click on "Preferences"
In "Mode" make sure "Hotmail Live (New website)" is selected
In "POP" tab, i've got "Mark emails as read on server" & Download JunkMail" Ticked. (Rest are blank)
In "SMTP" tab, i've got "Send plain text" selected.

In the "Domains" tab make sure your hotmail domain is listed, if not add it.

Close the windows and restart thunderbird.

you should be able to pick up hotmail now.
If not check the logs to see if there is any probems..

---

### Post by SunnyRabbiera on 2008-08-06
Yeh I remember doing something like that when I used hotmail in Thunderbird a few years back.

---

### Post by dragonlord2598 on 2008-08-06
> **solitaire said:**
> OK

Start "ThunderBird" go to "Edit" then "Account Settings"
Click on "Add Account"
Select "Web Mail", click "Next"
enter in your name and your hotmail address click "Next"
enter your hotmail address and click "Next"
Then click "Finish"

In "Thunderbird" then go to "Tools" / "Add-ons"
select "WebMail" and click on "Preferences"

In the "Servers" tab "POP" & "SMTP" should be "Running"
ports:
POP : 1100
SMTP: 2500
Make sure "Enable at startup" is ticked for both of these.

IMAP should be "Stopped" .

Click "Close"

Go to "WebMail - Hotmail" and click on "Preferences"
In "Mode" make sure "Hotmail Live (New website)" is selected
In "POP" tab, i've got "Mark emails as read on server" & Download JunkMail" Ticked. (Rest are blank)
In "SMTP" tab, i've got "Send plain text" selected.

In the "Domains" tab make sure your hotmail domain is listed, if not add it.

Close the windows and restart thunderbird.

you should be able to pick up hotmail now.
If not check the logs to see if there is any probems..

I dont have the choice of selecting "webmail" any where when i add an account i have the the choice of e-mail account

---

### Post by solitaire on 2008-08-06
What versions of Thunderbird and the WebMail add ons do you have?

---

### Post by dragonlord2598 on 2008-08-06
> **solitaire said:**
> 

Go to "WebMail - Hotmail" and click on "Preferences"
In "Mode" make sure "Hotmail Live (New website)" is selected
In "POP" tab, i've got "Mark emails as read on server" & Download JunkMail" Ticked. (Rest are blank)
In "SMTP" tab, i've got "Send plain text" selected.

In the "Domains" tab make sure your hotmail domain is listed, if not add it.

Close the windows and restart thunderbird.

you should be able to pick up hotmail now.
If not check the logs to see if there is any probems..

OK got here now im confused. HELP....ME...PLS...


jmol

---

### Post by dragonlord2598 on 2008-08-06
uuuu idk

---

### Post by dragonlord2598 on 2008-08-06
version 2.0.0.16 (20080724)

---

### Post by dragonlord2598 on 2008-08-06
Web-Mail-1.3.2

---

### Post by solitaire on 2008-08-06
What bit are you stuck at?

In the "add ons" page you should see 2 Webmail entries
1) WebMail 1.3.2
2) WebMail - Hotmail  1.2.18

In the section you posted above select "WebMail - Hotmail" in the Add ons page.

if you do not have "WebMail - Hotmail" then you need that to pick up from Hotmail... :D

Download the Latest Hotmail Add ons for Webmail here:
[http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html)

---

### Post by dragonlord2598 on 2008-08-06
Web-Mail-1.3.2
version 2.0.0.16 (20080724)

---

### Post by dragonlord2598 on 2008-08-06
Connection to server localhost timed out.


The msg that i get

---

### Post by solitaire on 2008-08-06
Sounds like your machine can't see the webmail addons properly.

have you looked at this thread:
[http://ubuntuforums.org/showthread.php?t=748105&highlight=WebMail](http://ubuntuforums.org/showthread.php?t=748105&highlight=WebMail)
the Attachment in the first post is a "How-To" for Hotmail via Thunder bird.

I used it to get my Hotmail working.

Give it a read..

---

### Post by northern lights on 2008-08-06
@solitaire:

Man after reading your post on the webmail plugin I got quite curious.

Yesterday I went to have dinner at my parents place. My mother's a teacher, but pretty computer-retarded. The uses Windows Live Hotmail and compains about the nature of the address book. I tried to get it to work with her Outlook (she's got the MS Office Suite installed). Failed. A Microsoft product should connect to a Microsoft service out of the box, you'd think.

Anyway, I got it to work for her yesterday. Very simple plugins.

Thanks mate.


@dragonlord (the OP):

Go back to the webmail site and download the Hotmail plugin it seems not to be installed. You need both, the general Webmail and [this]("http://download.mozdev.org/webmail/hotmail-1-2-18.xpi") (right-click to download).

---

### Post by solitaire on 2008-08-06
Glad to be of service. :D:D

F.Y.I. 
The Hotmail link to Outlook and outlook express is a $ubscription $ervice from Micro$oft! (who would have guesed!...;) )

---

### Post by northern lights on 2008-08-06
> **solitaire said:**
> The Hotmail link to Outlook and outlook express is a $ubscription $ervice from Micro$oft! (who would have guesed!...;)
Ended up on that website also, left immediately.

My mother's Windows isn't even pirated, it shipped with the comp. Still, I refuse to pay extra accessing email via POP. Please.

---

### Post by madsc89 on 2008-10-07
I couldn't get it working either, but then I followed the guide refereed to by solitaire ([http://ubuntuforums.org/showthread.p...hlight=WebMail](http://ubuntuforums.org/showthread.p...hlight=WebMail)), and it worked like a dream. Those of you who are still struggling, try that one. I got one correction to the guide, however; I couldn't get green lights on port 2500, so I used 2501. Just remember to stick to the number of your choice if you do the same;) 

Thank you

---

