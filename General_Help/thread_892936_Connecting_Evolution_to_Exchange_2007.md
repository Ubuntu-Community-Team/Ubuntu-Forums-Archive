---
title: "Connecting Evolution to Exchange 2007?"
date: 2008-08-17
forum: General Help
---

### Post by antknee869 on 2008-08-17
Hi I am running 8.0.4.1. Is it possible to connect Evolution to Exchange 2007? I know the OWA url and I can log in to OWA fine. However the Evolution setup does not connect to Exchange. 
I have searched and know there are multiple issues with this setup, but none mention Exchange 2007 specifically so I wonder if I am just wasting my time.
Thanks

---

### Post by antknee869 on 2008-08-19
Anyone?? Hello??  :)

---

### Post by ooobuntooo on 2008-08-19
It works fine for me. There is a MS Exchange option when creating an account in Evolution.

---

### Post by Titan8990 on 2008-08-19
Yes, its the same as any other POP or IMAP server even if it doesn't comply with certain internet standards.

---

### Post by antknee869 on 2008-08-19
Well, it doesn't work for me. It gives me an error: Could Not Find Server. But I can log in to OWA fine.

---

### Post by foresto on 2008-08-28
Keep in mind here that the original poster's Exchange server might not allow POP or IMAP clients, and even if it does, that wouldn't give access to the Global Address List or calendar features of Exchange.  Also, I think it's pretty well known that Evolution's current Exchange connector doesn't work with Exchange 2007.

Here's the good news:

The [OpenChange]("http://www.openchange.org/") project has been working on open source code (libmapi) that will connect to Exchange using the same network protocol that Outlook uses.  It was [recently accepted]("http://packages.qa.debian.org/o/openchange.html") into Debian's package system.  There is now a [sync request]("https://bugs.launchpad.net/ubuntu/+bug/260786") to bring that code into Ubuntu.  I have read reports that a new Evolution/Exchange connector that uses libmapi is on its way, perhaps as early as Evolution 2.23.

In short, it looks like help is on the way.  Assuming there is sufficient demand and people willing and able to do the remaining work, I'm guessing we'll see this stuff in the next few months.

---

### Post by antknee869 on 2008-08-28
So it requires POP & IMAP to be active on Exchange 2007? If so, those are disabled by default so that is my problem.

---

### Post by Alex53 on 2008-09-16
I am on the same boat. I am using Exchange 2007. The error I get says something along the lines of 'You are using Exchange 5.5, this connector only supports Exchange 2000 and 2003', obviously it doesnt know about 2007 :(

Would you explore other options to get Exchange going (not via POP, but a more complete solution with calendar, tasts, global address book, etc) or should I wait until Evolution supports 2007? How long am I looking at?

---

### Post by zoomy942 on 2008-09-24
i tried the owa method from onsite and it wouldnt work.  but the IMAP one works.

the problem is, when i delete items on it they dont delete off the server.  this is a problem becuase then my blackberry is out of sync.

and the buttons on the bottom left dont show what they should - meaning Contacts doesnt show contacts

---

### Post by Larsko on 2009-04-26
Hi Guys,

After a little bit of Googeling I found the following sollution..

[http://packages.ubuntu.com/jaunty/i386/evolution-mapi/download](http://packages.ubuntu.com/jaunty/i386/evolution-mapi/download)

It's a great package that gives you an extra option in your connection list when you create a new Evolution account.

This "plugin" lets you connect to your Exchange 2007 server.

Unfortunately it doesn't support calendar syncing since it is using MAPI.

Cheers,

Lars

---

### Post by mrjawbones on 2009-04-30
I have that package installed already and when I try the MAPI method, as soon as I authenticate, Evolution just disappears and when I launch it again, it goes through the initial account setup all over again.  When I try the OWA method, I get this error (see attached).

If anyone has any ideas, I would greatly appreciate it.  Thanks.

---

### Post by Larsko on 2009-05-02
Hi Guys,

I took a closer look at this problem and discovered that the agenda feature is supported, but is still full of bugs at the moment.

This means that it will synchronise your agenda without problems, but when it tries to sync your agenda it will fail and tell you something like the connection is lost and that you will need to restart Evolution.

When I've found the bugfix I will post my comments in this section of the forum.

Cheers!!

Lars

---

### Post by Larsko on 2009-05-02
Hi mrjawbones,

The error that you get is because Exchange 2003 uses a different kind of connection / authentication.

This is the reason Evolution has build a new plugin (the one you have installed).

I suppose you already took the upgrade to Jaunty Jackalope and are working with the last version (Version 2.26.1) of Evoluition?

What could cause the problem is your connection.

If you connect to your Exchange server via the External IP it could cause this problem.

What you can do (if you didn't already did it) is reïnstall the MAPI plugin and purge all configuration files.

You can do this in Synaptic Packagemanager or bij Commandline (sudo apt-get remove evolution-mapi --purge and then sudo apt-get install evolution-mapi).

Good Luck!!

Cheers,

Lars

---

### Post by Fuchur777 on 2009-05-13
Hi All,

Did a fresh install of Evolution 2.26.1 and the evolution-mapi.

Fired up Evolution made a brand new account.
- Don't use the servername but its IP
- Username
- Domain
It then does connect with me while I am in the network.

Calendar/Contacts and Mail are working!

Will try through vpn later today...

Ta Frank

---

### Post by Larsko on 2009-05-13
Hi Guys,

A employee of a customer of us had the same issue as mrjawbones.

This was fixed by using the IP address instead of the hostname of the Exchange server.

When you use Jaunty Jackalope and the latest update of the evolution-MAPI plugin all modules work, even the agenda and the notes will work!!

The only thing that doesn't work 100% is using the Evolution-MAPI when you are connected by VPN.

Special thanks to Fuchur for the sollution!!

Cheers,

Lars

---

### Post by lhbecker on 2009-05-14
> **antknee869 said:**
> Hi I am running 8.0.4.1. Is it possible to connect Evolution to Exchange 2007? I know the OWA url and I can log in to OWA fine. However the Evolution setup does not connect to Exchange. 
I have searched and know there are multiple issues with this setup, but none mention Exchange 2007 specifically so I wonder if I am just wasting my time.
Thanks

I have the same question. I am able to access Exchange using the OWA on Firefox under ubuntu, but Firefox warns that the Website Certificate is out of date and I have to accept the out-of-date certificate before I can use OWA. I am assuming that I am not able to authenticate in Evolution because of this. Is there a way to accept out-of-date certificates in Evolution?

---

### Post by Larsko on 2009-05-17
Hi lhbecker,

I had the same problem before.

When you permanently accept the certificate in Firefox, Evolution will be able to connect to your exchange server without any problems.

What you can do is ask the administrator of the Exchange server to buy a certificate ([http://www.godaddy.com](http://www.godaddy.com) or [http://www.sslcertificaten.nl](http://www.sslcertificaten.nl)) this should solve the certificate problem.

But as I mentioned before this is not necessary.

Cheers!!

Lars

---

