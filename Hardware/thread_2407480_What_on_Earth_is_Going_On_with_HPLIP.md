---
title: "What on Earth is Going On with HPLIP?"
date: 2018-12-04
forum: Hardware
---

### Post by mattlach on 2018-12-04
So, 

I usually need to manually download HPLIP in order to get the latest drivers.

For years I have had no problems.

This time, the official webpage ([https://developers.hp.com/hp-linux-imaging-and-printing](https://developers.hp.com/hp-linux-imaging-and-printing)) is not responding.  I did a whois, and thedomain, doesn't even seem to be registered?

Luckily, I found that I can still get the latest releases from the sourceforge page ([https://sourceforge.net/projects/hplip/](https://sourceforge.net/projects/hplip/))

When I do - however - it fails to download the required plugin, presumably due to mot being able to find the url where it is stored.

is anyone else having this problem?

---

### Post by ajgreeny on 2018-12-05
Works fine here; check your network connection and maybe firewall if you have it activated.

I have had problems in the past getting an additional required plugin for a printer but have not needed one for many years; if you have hplip installed see if using the setup from hplip-toolbox helps.  You may need to install hplip-gui to get that but it can also be run from command-line I think though I'm not sure of command needed.

See if this bug helps with your problem.
[https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/1749690](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/1749690)

---

### Post by coffeecat on 2018-12-05
> **mattlach said:**
> 
This time, the official webpage ([https://developers.hp.com/hp-linux-imaging-and-printing](https://developers.hp.com/hp-linux-imaging-and-printing)) is not responding.  I did a whois, and thedomain, doesn't even seem to be registered?

I can confirm that your link works just fine for me too. Also, whether I do a whois on just the domain - [noparse]hp.com - or include the sub-domain - developers.hp.com - I get information for hp.com. It would be surprising indeed if hp.com was not registered! Curious that you can't get hp.com to resolve and a whois gives you no information. Which whois site were you using?
[/noparse]

---

### Post by mattlach on 2018-12-05
> **coffeecat said:**
> I can confirm that your link works just fine for me too. Also, whether I do a whois on just the domain - [noparse]hp.com - or include the sub-domain - developers.hp.com - I get information for hp.com. It would be surprising indeed if hp.com was not registered! Curious that you can't get hp.com to resolve and a whois gives you no information. Which whois site were you using?
[/noparse]

That is really odd.

The top level domain (hp.com) resolves just fine for me, but developers.hp.com has no response at all on any device on my network with VPN on (via PIA) VPN off (Verizon FiOS) or using the mobile network on my phone (Google Fi)

I wonder if my DNS is messed up...

I was using whois from the console:

```
~ $ whois developers.hp.com
No match for "DEVELOPERS.HP.COM".
>>> Last update of whois database: 2018-12-05T21:50:17Z <<<

NOTICE: The expiration date displayed in this record is the date the
registrar's sponsorship of the domain name registration in the registry is
currently set to expire. This date does not necessarily reflect the expiration
date of the domain name registrant's agreement with the sponsoring
registrar.  Users may consult the sponsoring registrar's Whois database to
view the registrar's reported date of expiration for this registration.

TERMS OF USE: You are not authorized to access or query our Whois
database through the use of electronic processes that are high-volume and
automated except as reasonably necessary to register domain names or
modify existing registrations; the Data in VeriSign Global Registry
Services' ("VeriSign") Whois database is provided by VeriSign for
information purposes only, and to assist persons in obtaining information
about or related to a domain name registration record. VeriSign does not
guarantee its accuracy. By submitting a Whois query, you agree to abide
by the following terms of use: You agree that you may use this Data only
for lawful purposes and that under no circumstances will you use this Data
to: (1) allow, enable, or otherwise support the transmission of mass
unsolicited, commercial advertising or solicitations via e-mail, telephone,
or facsimile; or (2) enable high volume, automated, electronic processes
that apply to VeriSign (or its computer systems). The compilation,
repackaging, dissemination or other use of this Data is expressly
prohibited without the prior written consent of VeriSign. You agree not to
use electronic processes that are automated and high-volume to access or
query the Whois database except as reasonably necessary to register
domain names or modify existing registrations. VeriSign reserves the right
to restrict your access to the Whois database in its sole discretion to ensure
operational stability.  VeriSign may restrict or terminate your access to the
Whois database for failure to abide by these terms of use. VeriSign
reserves the right to modify these terms at any time.

The Registry database contains ONLY .COM, .NET, .EDU domains and
Registrars.

```

---

### Post by ajgreeny on 2018-12-06
Using the whois in terminal I get exactly the same output as you, nevertheless going to that url in a browser is no problem so I'm not sure what that means unless as you suggest your DNS is somehow faulty.

Could it be a VPN problem?

---

### Post by ajgreeny on 2018-12-06
To add to my post #5 I have just tried [http://whois.domaintools.com/](http://whois.domaintools.com/) in a browser and searched for **developers.hp.com** there, and it finds it with no problem.

---

