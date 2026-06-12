---
title: "Gmail smtp server don't work in thunderbird and evolution"
date: 2008-07-24
forum: General Help
---

### Post by david sousa on 2008-07-24
Hello!

My problem is that i cant send any e-mail but i can recieve it with no problems. I allready veryfied de protocols and doors a thousand times, But it simply doesn't work!

I get the error:

Sending of message failed. The message could not be sent because connecting to SMTP server smtp.gmail.com failed. The server may be unavailable or is refusing SMTP connections. Please verify that your SMTP server setting is correct and try again, or else contact your network administrator.

And the solution exist for mocrosoft OS's but didn't find for linux.

Help me please! this is really annoying!

---

### Post by Potatoj316 on 2008-07-24
It works for me just fine.  You probably have some setting wrong.  Make sure your using the correct authentications and ports.

---

### Post by danwood76 on 2008-07-24
The google smtp servers use an odd port number.
Check the google help pages for setting up pop and make sure you set the port numbers correctly.

Ive had gmail setup in thunderbird for months and have had no issues.

---

### Post by artmendez on 2008-07-24
Have you checked if you Google preferences have POP enabled? Make sure you enable one of this options and SAVE your preferences.

BTW, my account doesn't show any selection on if you go back to check if it worked. I just do it, save it and trust it. Please share if same thing happens to you.

Word of advice, Google recently added IMAP enabling too. I enabled this to give it a try, and spoiled POP access from Evolution... I enabled again POP, disabled IMAP, saved preferences and it worked back.

Also, make sure you set your email client for SSL encryption.

If you upgraded Evolution, I think some of the fields in account configuration dialogs changed... specially as it doesn't specify a server port. Google POP requires SSL encryption. Receiving is no problem, but sending needs a port set. I solved also in Evolution by specifying the port within the SMTP server address like this: > **smtp.gmail.com:465**

I hope this helps.

saludos.

---

### Post by david sousa on 2008-07-24
I allready tryed everything you said as I said. Ports, encryption, everything... It's very atrange because it doesn't work with the both mail clients!

---

### Post by artmendez on 2008-07-24
Did you even try including the port with the SMTP server address?

I'm attaching a screenshot of my Evolution config. I'm using Evolution 2.22.3.1.

---

### Post by danwood76 on 2008-07-25
Attached is my config for Thunderbird, POP and SMTP.
It must be a configuration error, or you haven't properly enabled pop in your gmail control panel.

---

### Post by ingeva on 2008-07-29
Same problem.

I have set up my external SMTP servers with correct port numbers. Thunderbird gives Gmail port numbers "for free".

Either Thunderbird has a problem with port numbers for SMTP, or it doesn't like any kind of authentication (even plain username/password auth.).

If Evolution has the same problem, how to send any mail?
Will the only solution be to run a local SMTP server? If so, is there anyone recommended?

---

### Post by louieb on 2008-07-29
Check with your ISP, some like mine (ATT) block the normal smtp ports (25 and 465).  Forcing me to use ATTs'  smtp server.

In the case of ATT I could send them a letter asking for the block to be removed.

---

### Post by ingeva on 2008-07-29
> **louieb said:**
> Check with your ISP, some like mine (ATT) block the normal smtp ports (25 and 465). Forcing me to use ATTs' smtp server.
 
In the case of ATT I could send them a letter asking for the block to be removed.
 
The same ports work fine with my Windows computer and Outlook Express.
If I use my ISP's SMTP server there are no problems but it uses ports 25 and 110 and does not require authentication.
 
However, I move around and using the server on my webhost seems to be the easiest solution for global use.

---

### Post by danwood76 on 2008-07-29
Thunderbird works perfectly with gmail from here.
Never had any problems so it must be your ISP or a configuration error.

---

### Post by ingeva on 2008-07-29
> **danwood76 said:**
> Thunderbird works perfectly with gmail from here.
Never had any problems so it must be your ISP or a configuration error.

In order to move my mail data from the Windows machine I installed Thunderbird on it, and it turns out it has the same problem. So OE works, Thunderbird didn't.

However, some further investigation and comparing I found that it had set the wrong authentication type. After I corrected it to SSL sending with smtp.gmail.com was no problem (at port 465).

I find Evolution extremely clumsy to use, so I think I'm stuck with Thunderbird. :)

Since I didn't start this thread I won't close it or mark it solved. I haven't tried the other SMTP servers yet either, but I guess the problem with those is very similar to gmail's.

---

### Post by ingeva on 2008-07-29
Additional info:

I tried it with Evolution again. I get this error message:

host lookup failed: smtp.upandforward.com:Name or service not known

This is the server that I use all the time with OE without problems....

Thunderbird prints a more descriptive error message but states that the server may be down or is incorrectly configured. Based on the speed with which it accesses the server I doubt that it accesses the server at all! :)

Gmail works fine now, with both mail clients. I wonder why they won't process my own servers.

Any ideas?

---

### Post by chunchengch on 2008-07-29
try this,

Server  : [COLOR="Red"]smtp.gmail.com[/COLOR]
Port    : [COLOR="Red"]587[/COLOR]
Default : [COLOR="Red"]25[/COLOR]
Use secure connection : [COLOR="Red"]TLS[/COLOR]

---

### Post by ingeva on 2008-07-29
> **chunchengch said:**
> try this,

Server  : [COLOR=Red]smtp.gmail.com[/COLOR]
Port    : [COLOR=Red]587[/COLOR]
Default : [COLOR=Red]25[/COLOR]
Use secure connection : [COLOR=Red]TLS[/COLOR]

It finally worked with port 465 and SSL. It's the other SMTP servers that give me trouble now. :(
It seems like the mail programs don't even attempt to contact the server!

---

### Post by ingeva on 2008-07-29
> **ingeva said:**
> It finally worked with port 465 and SSL. It's the other SMTP servers that give me trouble now. :(
It seems like the mail programs don't even attempt to contact the server!


PROBLEM SOLVED!

It turns out that Thunderbird (Evolution too perhaps?) assumes the prefix "smtp", so if you type the full server name in the configuration, it won't find the server.

However, this does not happen with the local ISP (without authentication on port 25) and it does not happen with the gmail account.

So I set up my own servers with just the domain name and the port number (587). I also defined TLD security, which made me have to accept a certificate before the mail was accepted.

Since I have now made Thunderbird work and I have transferred all mail and address book to it, I have no wish to experiment more with Evolution.

---

### Post by athianos on 2008-07-30
> **ingeva said:**
> PROBLEM SOLVED!

So I set up my own servers with just the domain name and the port number (587). I also defined TLD security, which made me have to accept a certificate before the mail was accepted.
tion.

I had a problem sending mail with Thunderbird in Ubuntu using gmail.

Thank you! I am now able to send mail via smtp.gmail.com and my POP is working properly using the following settings.

smtp.gmail.com
567
TLS if available

:guitar:

I wonder if there was an update or something that changed settings. Mine stopped working 29th July. :confused:

---

### Post by karthik.velugoori on 2008-08-21
> **athianos said:**
> I had a problem sending mail with Thunderbird in Ubuntu using gmail.

Thank you! I am now able to send mail via smtp.gmail.com and my POP is working properly using the following settings.

smtp.gmail.com
567
TLS if available

:guitar:

I wonder if there was an update or something that changed settings. Mine stopped working 29th July. :confused:

hi these settings didn't work for me ...
i use thunderbird on Ubuntu 8.04(64bit) for gmail
friends in my lab have the same problem too...

and the same settings work pretty fine in my house(!!!!!)

---

### Post by danwood76 on 2008-08-21
If the settings work fine in your house but not in your lab and everyone in your lab has the same issue then its got to be to do with the internet connection in your lab as opposed to the settings.

---

### Post by Joeb454 on 2008-08-21
Most places like that won't allow POP3 or SMTP connections through their network.

The web based interface however - works fine :)

---

### Post by Ameneon on 2008-10-24
Got this exact same problem at home. Used to work just fine, then after some update (I don't send mail all that often so I didn't notice which update this was) it wouldn't send any longer. Gmail takes a little while to spin through while ISP smtp immediately pops up an error when trying to send, while both work fine in windows. I'll try the steps suggested here when I get home tonight to see if that helps.

---

### Post by ingeva on 2008-10-24
> **Ameneon said:**
> Got this exact same problem at home. Used to work just fine, then after some update (I don't send mail all that often so I didn't notice which update this was) it wouldn't send any longer. Gmail takes a little while to spin through while ISP smtp immediately pops up an error when trying to send, while both work fine in windows. I'll try the steps suggested here when I get home tonight to see if that helps.

It wasn't really that hard.

I use port 465 and SSL connection. Works like a charm.

---

### Post by dnzz on 2008-10-24
First port number is not 567 it is 587 

Second you should check your connection if it allows smtp protocol or not.

---

### Post by ingeva on 2008-10-24
> **dnzz said:**
> First port number is not 567 it is 587 

Second you should check your connection if it allows smtp protocol or not.

It pays to read earlier posts.

---

### Post by phewbuntu on 2009-01-12
This was happening to me too.  When I added the Gmail account, I used the default settings that Thunderbird provided.  The trick was to modify the outgoing server information.  For some reason, the security wasn't set to SSL and the port number wasn't 465.  By changing to those settings, everything worked fine.
-Phew

---

