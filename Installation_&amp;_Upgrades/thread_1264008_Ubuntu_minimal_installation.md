---
title: "Ubuntu minimal installation"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by MakLeod on 2009-09-11
So I've looked far and wide for a hard wired ethernet connection to use with my laptop and installing Ubuntu from a minimal installation (mini.iso), but have yet to find one.  I want to basically build my own system and have a slimmed down, streamlined installation.  However, I've found that I cannot do it with wireless as the system will not recognize it.  Is there any way to do the minimal installation through wireless or does it have to be through eth0?  Thanks!

---

### Post by mikewhatever on 2009-09-12
I don't know about installing via wireless, but why not consider an Alternate cd instead? It has an option, under F4, of installing the CLI system, to which you can later add packages from the very same cd.

---

### Post by raymondh on 2009-09-12
> **mikewhatever said:**
> I don't know about installing via wireless, but why not consider an Alternate cd instead? It has an option, under F4, of installing the CLI system, to which you can later add packages from the very same cd.

Or try the server edition and build from there.

---

### Post by snowpine on 2009-09-12
Hi MakLeod, it is absolutely possible to configure wireless from the command line. :)

Here is one of many tutorials on the subject: [http://crunchbang.org/archives/2007/12/18/configure-wireless-on-the-command-line/](http://crunchbang.org/archives/2007/12/18/configure-wireless-on-the-command-line/)

---

### Post by mikewhatever on 2009-09-12
> **snowpine said:**
> Hi MakLeod, it is absolutely possible to configure wireless from the command line. :)

Here is one of many tutorials on the subject: [http://crunchbang.org/archives/2007/12/18/configure-wireless-on-the-command-line/](http://crunchbang.org/archives/2007/12/18/configure-wireless-on-the-command-line/)

Just to clarify, snowpine is referring to configuring wireless on a command line installation. That's the thing to try once the base system is in place and you want to keep adding packages via the wireless. I don't know if it works with a mini.iso, simply because there is no way to run the required commands.

---

### Post by snowpine on 2009-09-12
> **mikewhatever said:**
> Just to clarify, snowpine is referring to configuring wireless on a command line installation. That's the thing to try once the base system is in place and you want to keep adding packages via the wireless. I don't know if it works with a mini.iso, simply because there is no way to run the required commands.

Good point--I didn't think about that. :)

Alternate CD then! :popcorn:

---

### Post by MakLeod on 2009-09-23
> **mikewhatever said:**
> Just to clarify, snowpine is referring to configuring wireless on a command line installation. That's the thing to try once the base system is in place and you want to keep adding packages via the wireless. I don't know if it works with a mini.iso, simply because there is no way to run the required commands.
So there's no way to use that tutorial after installing the base system with the mini.iso?  I can't remember at the moment, but does the mini.iso stop you from installing if there is no network configured?  Does the mini.iso supply a fully functioning command line environment complete with the kernel?  My guess is no considering it is only 10 megs...

---

### Post by boof1988 on 2009-09-23
> **MakLeod said:**
> So there's no way to use that tutorial after installing the base system with the mini.iso?  I can't remember at the moment, but does the mini.iso stop you from installing if there is no network configured?  Does the mini.iso supply a fully functioning command line environment complete with the kernel?  My guess is no considering it is only 10 megs...

To quote from [Ubuntu Communty Documentation - MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) indicates...

> To install, boot your computer from the the Minimal CD and type "cli" (command line install) at the prompt. You can then follow the instructions from the text-based installer.

From what I remember... one can install a functional CLI system by using the mini.iso (without network access).

Hope This Helps,

---

### Post by wojox on 2009-09-23
I've done this before it's fun, but you need a wired connection.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by snowpine on 2009-09-23
mini.iso is what's called a "netinstall"... it has just enough to pull the required files from the 'net. It is useless without a working internet connection.

You can use the Alternate CD to install a cli-only system if you don't have an internet connection.

---

