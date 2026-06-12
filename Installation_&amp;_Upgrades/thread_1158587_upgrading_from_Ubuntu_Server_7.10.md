---
title: "upgrading from Ubuntu Server 7.10"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by newbie_po_ako on 2009-05-13
We just had our mail server running on Ubuntu Server 7.10 last year. A computer company set it up for us and it's really pricey. Now it seems that this OS is no longer supported and we need to upgrade the OS. I am a newbie in Ubuntu, I only know a few basic terminal commands. I want to help our company save some money in having our server upgraded. Please advise where to start and how to do it. By the way, this computer is handling our email (using the following packages: postfix, dovecot, amavis, clamav and squirrelmail), proxy (using the SQUID proxy server) and firewall (using the SHOREWALL Firewall). 

Thank you and more power to Ubuntu team.

---

### Post by pastalavista on 2009-05-13
You can upgrade automatically to Ubuntu 8.04. If you're online just open a terminal and enter
```
sudo apt-get dist-upgrade
```

If your server was set up after April of last year, he should have used Hardy (8.04) anyway as it is a Long Term Service release, meaning it will be supported 5 yrs. for servers and 3 yrs. for desktops.

---

### Post by iaculallad on 2009-05-13
> **newbie_po_ako said:**
> We just had our mail server running on Ubuntu Server 7.10 last year. A computer company set it up for us and it's really pricey. Now it seems that this OS is no longer supported and we need to upgrade the OS. I am a newbie in Ubuntu, I only know a few basic terminal commands. I want to help our company save some money in having our server upgraded. Please advise where to start and how to do it. By the way, this computer is handling our email (using the following packages: postfix, dovecot, amavis, clamav and squirrelmail), proxy (using the SQUID proxy server) and firewall (using the SHOREWALL Firewall). 

Thank you and more power to Ubuntu team.

Why the need to upgrade? Do you observe any technical flaws that stops your server from performing its functions as installed? Well, if thats not the case, try not to consider the upgrade option. But if you still insist, you could perform pastalavista's suggestion and have your current server upgraded.

As for me, I'm happy with my Gutsy Server and I see no reason of upgrading it to later versions. Gutsy's serving our company's Apache, MySQL, PHP, and FTP needs.

---

### Post by newbie_po_ako on 2009-05-17
iaculallad: i think you're right. that's what i have in mind also. so far, nothing is screwed and everything is up and running (i think). i just have some noobie questions, since our os doesn't get any update anymore are my other applications also don't get updates? like our antivirus, firewall? where do i get supports for my os?

pastalavista: if ever i need to upgrade my os and do this in the terminal, do i also need to reconfigure the settings? will the other applications running in the server (like firewall, antivirus, etc.) need to be reinstalled?

---

### Post by pastalavista on 2009-05-18
> **newbie_po_ako said:**
> 
pastalavista: if ever i need to upgrade my os and do this in the terminal, do i also need to reconfigure the settings? will the other applications running in the server (like firewall, antivirus, etc.) need to be reinstalled?

I have never lost any data or config files from an update like that, but I have lost some hardware driver functionality like wireless and graphics cards. I believe that as long as you select only important and recommended updates and only supported software sources, no proposed or restricted, third-party etc. you would probably benefit from it. Also, don't overwrite the boot for the previous kernel and you can revert to the old setup. It may not be perfect and could possibly go horribly wrong, but it shouldn't lose data.. the problem would be too much conflicting data. Backing things up should always be first, so don't do anything you aren't sure of. Starting over from scratch isn't fun but sometimes it can be for the best... if you have the data safe and sound.

---

### Post by newbie_po_ako on 2009-05-18
> **pastalavista said:**
> I have never lost any data or config files from an update like that, but I have lost some hardware driver functionality like wireless and graphics cards. I believe that as long as you select only important and recommended updates and only supported software sources, no proposed or restricted, third-party etc. you would probably benefit from it.

I AM FEELING SCARED ALREADY!!!

> **pastalavista said:**
> Also, don't overwrite the boot for the previous kernel and you can revert to the old setup. It may not be perfect and could possibly go horribly wrong, but it shouldn't lose data.. the problem would be too much conflicting data.

How do I do this? 

> **pastalavista said:**
> Backing things up should always be first, so don't do anything you aren't sure of. Starting over from scratch isn't fun but sometimes it can be for the best... if you have the data safe and sound.

All I back up now is from /home directory. Will this be enough? OMG, I'm such a noob. :(

---

### Post by dmizer on 2009-05-18
> **newbie_po_ako said:**
> We just had our mail server running on Ubuntu Server 7.10 last year. A computer company set it up for us and it's really pricey. Now it seems that this OS is no longer supported and we need to upgrade the OS. I am a newbie in Ubuntu, I only know a few basic terminal commands. I want to help our company save some money in having our server upgraded. Please advise where to start and how to do it. By the way, this computer is handling our email (using the following packages: postfix, dovecot, amavis, clamav and squirrelmail), proxy (using the SQUID proxy server) and firewall (using the SHOREWALL Firewall). 

Thank you and more power to Ubuntu team.

In this situation, I would highly suggest taking your time and researching everything very very carefully. I also suggest testing your upgrade before actually doing it live, and I suggest you contact someone from your linux lug ([http://www.linux.org/groups/](http://www.linux.org/groups/)) or loco ([https://wiki.ubuntu.com/LoCoTeams](https://wiki.ubuntu.com/LoCoTeams)) to get some in person advice from knowledgeable users.

For testing, you can image the server: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Then convert your server into a virtual machine: [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

Then you can have a copy of your server you can test with without the worry of breaking something. Test all the implementations you like. Upgrade as many times as you like. Your live server will continue to be live and you will learn all you need for your upgrade.

---

### Post by pastalavista on 2009-05-18
> **newbie_po_ako said:**
> I AM FEELING SCARED ALREADY!!!



How do I do this? 



All I back up now is from /home directory. Will this be enough? OMG, I'm such a noob. :(

It's been too long since I ran a server so I'll defer [to the experts]("http://www.ubuntugeek.com/upgrade-ubuntu-710-gutsy-gibbon-to-ubuntu-804-lts-hardy-heron.html"). Good luck. And I'll give this post a BUMP so maybe more experts can help you out.. I'm not even close to an expert..

---

### Post by newbie_po_ako on 2009-05-18
I will DEFINITELY do this... Thanks guys for the links and advices.. More power!

---

### Post by newbie_po_ako on 2009-05-19
I'm back again..

what if our system doesn't support any gui? all i can see is the terminal...

---

### Post by dmizer on 2009-05-19
Converting the server into a virtual machine won't require a gui. Whatever you do, don't install a GUI. None of the services on the server will be configurable via GUI anyway.

Just make a copy of the machine, put it in a virtual environment for testing, and try upgrading it.

---

