---
title: "Cannot enter WebGUI with Transmission 1.61"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by mocka on 2009-06-01
I have recently installed Transmission 1.61. Eventhough I edit the settings.json file and set the right values, I can not access the WebGUI from specified port. Anyhow, when I enter the standard url ([http://192.168.0.185:9091/transmission/webgui](http://192.168.0.185:9091/transmission/webgui) (note the port)), it shows up a page that displays the following:

> 
403: Forbidden

Unauthorized IP Address.

Either disable the IP address whitelist or add your address to it.

If you're editing settings.json, see the 'rpc-whitelist' and 'rpc-whitelist-enabled' entries.

If you're still using ACLs, use a whitelist instead. See the transmission-daemon manpage for details.

What should I do to get it right?

I have tried both to disable whitelist and whitelist my own ip there.

---

### Post by gordintoronto on 2009-06-01
Your server is at 0.185?

To be honest, I don't understand why anybody needs the webgui.  Transmission works fine without it.

> **mocka said:**
> I have recently installed Transmission 1.61. Eventhough I edit the settings.json file and set the right values, I can not access the WebGUI from specified port. Anyhow, when I enter the standard url ([http://192.168.0.185:9091/transmission/webgui](http://192.168.0.185:9091/transmission/webgui) (note the port)), it shows up a page that displays the following:



What should I do to get it right?

I have tried both to disable whitelist and whitelist my own ip there.

---

### Post by mocka on 2009-06-02
Yes, my server is at 192.168.0.185. The reason I need the WebGUI is because I'm running a headless server (ie. a computer without a monitor).

EDIT:

I followed the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=1021120&highlight=transmission+json&page=2](http://ubuntuforums.org/showthread.php?t=1021120&highlight=transmission+json&page=2)

I typed the following in terminal:

```

transmission-daemon -p 9091 -f -T -a 192.168.0.185

```

That made me able to enter the WebGUI. But then, if I try to turn on the normal daemon (sudo /etc/init.d/transmission-daemon start) I just get the same error as before.

Any suggestions?

---

### Post by mocka on 2009-06-04
Anyone, no?

---

### Post by jvin248 on 2009-06-30
I found while testing that I had multiple instances of transmission-daemon running, older ones with prior non-working config files.

Install 'htop' and then scroll down and find lines with 'transmission' and F9 SIGKILL them. You can use regular old 'top' but I find htop works a bit easier.

I couldn't get into the browser gui (401 error), tried your command line you listed and it put up errors (errors I might use to solve the problem - like ports blocked by other programs). I used htop to delete the still open instances I found, then re-ran the command line and it started and I could see the browser gui.  Then I found the jason.conf file was changed automatically. I quit the command line version, killed it via htop, and restarted 'transmission-daemon' and it now works.

maybe that helps you.

---

### Post by jnbptst on 2009-11-14
I have the same issue. Although the whitelist is disabled and the authorized IP is set to *.*.*.*, I get a 401 error whenever I try to access the webGUI, whether from the local network or from Internet.

any help?

---

