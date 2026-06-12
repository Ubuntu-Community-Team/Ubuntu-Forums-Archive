---
title: "cups-bjnp?"
date: 2008-07-27
forum: General Help
---

### Post by LegosJedi on 2008-07-27
Alright, I'm new to Ubuntu. I'm trying to get a PC transfered to Ubuntu. We have a Canon MX700 printer, and, upon searching the forums, found instructions on making it play nice with Ubuntu. The problem is that it needs cups-bjnp to work, and, being new to Ubuntu, and even Linux, I don't know where to get this. Where DO I download it?

---

### Post by llagendijk on 2008-08-01
> **LegosJedi said:**
> Alright, I'm new to Ubuntu. I'm trying to get a PC transfered to Ubuntu. We have a Canon MX700 printer, and, upon searching the forums, found instructions on making it play nice with Ubuntu. The problem is that it needs cups-bjnp to work, and, being new to Ubuntu, and even Linux, I don't know where to get this. Where DO I download it?
[www.fazant.net/cups](www.fazant.net/cups)

---

### Post by LegosJedi on 2008-08-02
Thank you!

---

### Post by llagendijk on 2008-08-07
> **llagendijk said:**
> [www.fazant.net/cups](www.fazant.net/cups)

cups-bjnp-0.1 is now available from source forge!


[http://sourceforge.net/projects/cups-bjnp/](http://sourceforge.net/projects/cups-bjnp/)
2008-08-07 First beta release of CUPS-bjnp.

Cups-bjnp is a backend for CUPS that adds support for the Canon proprietary BJNP printing protocol.
It is based on the CUPS socket backend. The support of the BJNP protocol is based on reverse engineering
of the protocol, using TCP/IP dumps.
This release adds a number of additions over the versions released before on fazant.net:
- Adds spec files for Fedora and Centos 5 (RHEL5)
- Compiles without the need for the CUPS sources
- Supports CUPS 1.2 and 1.3 with the same source files

Ink level support is not included but planned to be added to Turboprint

---

