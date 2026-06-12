---
title: "apt-get Couldn't find package vsftpd"
date: 2008-10-19
forum: General Help
---

### Post by latrosicarius on 2008-10-19
Hello, when i was reading 2 tutorial pages on how to install vsftpd and they both said type **sudo apt-get install vsftpd**.

but this is the output:```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package vsftpd
```

In the archive section somebody else had this problem too, but nobody replied with a solution:
[http://ubuntuforums.org/showthread.php?t=467075](http://ubuntuforums.org/showthread.php?t=467075)

---

### Post by ranch hand on 2008-10-19
I just checked in my synaptic and it is listed there.

I am running hardy with all repositories enabled.

Did you do a-  sudo apt-get udate -?

---

### Post by bapoumba on 2008-10-19
[http://packages.ubuntu.com/search?keywords=vsftpd&searchon=names&suite=hardy&section=all]("http://packages.ubuntu.com/search?keywords=vsftpd&searchon=names&suite=hardy&section=all")
Should be in the main section.

Please post your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by latrosicarius on 2008-10-19
Hi, here is what happens when i try to update.

IDK why, i connect with it via PuTTY over WAN from a remote location.

I have a windows 2003 computer there too.  The Windows box resolves IP addresses just fine.  But anyway, I remoted in, and changed the router's DNS from default ISP to openDNS.  but the linux box is still getting the same errors that it cannot resolve the domain.

[[IMG]http://img252.imageshack.us/img252/1131/dnsfg4.png[/IMG]](http://imageshack.us)
[[IMG]http://img252.imageshack.us/img252/dnsfg4.png/1/w675.png[/IMG]](http://g.imageshack.us/img252/dnsfg4.png/1/)



Also, here is my sources.list

[[IMG]http://img374.imageshack.us/img374/2227/sourceskc5.png[/IMG]](http://imageshack.us)
[[IMG]http://img374.imageshack.us/img374/sourceskc5.png/1/w675.png[/IMG]](http://g.imageshack.us/img374/sourceskc5.png/1/)

---

### Post by ranch hand on 2008-10-19
Can you connect to other sites - anything?

Do you have some other program running that can access your repositories?

---

### Post by latrosicarius on 2008-10-19
> **ranch hand said:**
> Can you connect to other sites - anything?

Do you have some other program running that can access your repositories?

i don't know what is a command that will let me test if i can access another site?

---

### Post by ranch hand on 2008-10-19
I was just wondering if you had a connection.

If you have symantic open, not doing anything but open, you may have your problem, there are other apts that also connect ot the repositories, they should be closed.

This does not always cause a problem but it may and I thought you should check that.

You really need to have a connection though and what you posted makes it look like you may not have.

---

### Post by latrosicarius on 2008-10-19
what is the command to test if i have a connection?

---

### Post by ranch hand on 2008-10-19
Just try your browser, check the weather.  I do a lot of that as I work outside and needto be prepared.

I was goingto say check your conection speed but that shouldn't matter unless, like me, you are still on dial up.

---

### Post by latrosicarius on 2008-10-20
i dont have a browser... this is a CLI only version of ubuntu server and if it does have some sort of text-based browser, i don't know of it.

---

### Post by Zylar on 2008-10-20
Make sure /etc/resolv.conf has the same DNS servers listed as the 2k3 box.

You can use ping to see if names are being resolved.  Try 'ping ubuntuforums.org' and see if it resolves the address.

Your SSH session is using IPs, not domain names, and that's why it works (I would guess).

Good luck,

---

### Post by oldos2er on 2008-10-20
> **latrosicarius said:**
> i dont have a browser... this is a CLI only version of ubuntu server and if it does have some sort of text-based browser, i don't know of it.

 Lynx.

---

### Post by latrosicarius on 2008-10-20
> **Zylar said:**
> Make sure /etc/resolv.conf has the same DNS servers listed as the 2k3 box.

You can use ping to see if names are being resolved.  Try 'ping ubuntuforums.org' and see if it resolves the address.

oh, the 2k3 doesnt specify a DNS server.  it just gets it from the router... so shouldn't the linux do it too?

BTW, i can ping fine from the router:
[[IMG]http://img93.imageshack.us/img93/2093/pingroutervi1.png[/IMG]](http://imageshack.us)
[[IMG]http://img93.imageshack.us/img93/pingroutervi1.png/1/w522.png[/IMG]](http://g.imageshack.us/img93/pingroutervi1.png/1/)

but i cannot ping the same thing from the linux, although if i ping the resolved IP directly, it works:
[[IMG]http://img264.imageshack.us/img264/7820/pingou9.png[/IMG]](http://imageshack.us)
[[IMG]http://img264.imageshack.us/img264/pingou9.png/1/w675.png[/IMG]](http://g.imageshack.us/img264/pingou9.png/1/)


btw, the ping doesnt stop lol wtf

> **Zylar said:**
> Your SSH session is using IPs, not domain names, and that's why it works (I would guess).
actually i connect over WAN through a domain i registered.

---

### Post by ranch hand on 2008-10-20
I am back from riding all day.  We ship calves Wednesday.  You are welcome to your next steak.

I know a couple of ways to check a connection with a modem but don't know how to test yours as I don't know what connection you have, you should post that, but I wouldn't know then.

I co not have time to go through this stuff but her are some links that may help;

<http://www.karakas-online.de/gnu-linux-tools-summary/>

<http://www.karakas-online.de/gnu-linux-tools-summary/>

<http://www.karakas-online.de/gnu-linux-tools-summary/internet-specific-commands.html>

<http://www.karakas-online.de/gnu-linux-tools-summary/internet-specific-commands.html>

<http://www.tuxfiles.org/linuxhelp/manpages.html>

<http://www.ss64.com/bash/>

I hope these are a help.

It sounds to me that you do have a connection through your site.  Is there any kind of filter or firewall on that site?

---

### Post by latrosicarius on 2008-10-20
thanks.. that's cool about riding the horses and thanks for the steak :)

I'll give those links you gave me a shot.  Appreciate it!

---

### Post by Zylar on 2008-10-20
Try adding "nameserver <ip of router>" (without quotes) to /etc/resolv.conf.
(sudo nano /etc/resolv.conf)

Ctrl-c to stop pinging.

If you plan on hosting a FTP site, I'd suggest a static IP too.

Good luck,

---

### Post by latrosicarius on 2008-11-04
thank you very much zylar, that worked great and the ctrl-c thing too :)

---

