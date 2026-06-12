---
title: "Sending e-mail from multiple locations"
date: 2008-08-07
forum: General Help
---

### Post by toMeloos on 2008-08-07
Hi,

I regularly use my laptop to go online at different places and check my e-mail using Evolution, in which I have multiple e-mail accounts.

Different locations result in different ISP's and firewall settings. Some mailboxes require me to use my regular ISP's SMTP server for sending mail and some places I use Ubuntu (like the office) at even have a firewall that already blocks outbound SMTP traffic to prevent spamming.

My question is: is there a way to arrange that I can send my e-mail from anywhere without having to change the smtp settings of all my accounts every time and that works even with firewall-blocking of SMTP?

I was thinking some kind of tunneling system, proxy, anonymous thing or something. I don't really have a publicly accessable server to tunnel to at this time. Used the Gmail SMTP servers for all my accounts for a while until they changed the addressing last year making all my sent mails look like they came from my Gmail account. Besides, this doesn't solve the firewalling port 25 issue. :(

---

### Post by toMeloos on 2008-08-10
bump!

---

### Post by pierref on 2008-12-02
Hi toMeloos

I solved the problem in this way: 
1. I configured all my mail agents to use "localhost" as SMTP server on my laptop. 
2. I installed and configured postfix for trying a list of existing SMTP servers I have to introduce manually. Depending on where I connect my laptop, one of these SMTP servers is supposed to work, because the ISP normally allows the outgoing traffic on port 25 directed to their own SMTP relay.

This works fine. Before you start, collect the (fully qualified) list of hostnames of the SMTP servers you use for the several locations where you connect your laptop. In my case (Belgium), it is: ```
relay.chello.be, relay.dommel.be, relay.scarlet.be, relay.skynet.be
```

These are the detailed steps I have to perform:

install postfix:
```
sudo apt-get install postfix
```

If postfix is already installed, you can reconfigure it with the command:
```
sudo dpkg-reconfigure postfix
```

The configuration utility has a first screen that explains what's following. Go on.

At the second screen, select the option "Internet with smarthost" and go on.

At the next screen, leave the hostname of your host as is, except in the case you know better.

At the fourth screen, this is important, introduce the hostname of your first SMTP server. In my case ```
relay.chello.be
```

For all the remaining screens, just accept the default settings.

When you leave the configuration utility, there is only one SMTP server working, the first of your list. To add other servers, just edit the configuration file of postfix, with any command. I use gvim:
```
sudo gvim /etc/postfix/main.cf
```

Retrieve the line starting with ```
relayhost = 
```
and add a line with a comma separated list of the remaining servers as follows:
```
smtp_fallback_relay = relay.skynet.be, relay.dommel.be, relay.scarlet.be

```

Save the file and reload the configuration by issuing the command:
```
/etc/init.d/postfix reload
```

Now postfix is finding by itself a working SMTP server out of the list you provided. The order in which it tries is obviously first the variable $relayhost and then the variable $smtp_fallback_relay in the order of the list.

Each time you discover a location with a new SMTP server, add it in the configuration file and reload postfix. One day, someone will write a little script with a dialog to do that.

Et voilà!

---

