---
title: "HELP - Server Monitor screen???"
date: 2006-03-09
forum: Hardware &amp; Laptops
---

### Post by MJSOnline on 2006-03-09
Hi all.  Just a question.  I am hopfuly going to setup a home server to download files to and share files.  Can my laptop, that may dual boot, be used a screen for it?  Saving me some money of buting a flat panel screen.

---

### Post by Aine on 2006-03-09
If I'm understaning correctly, you want to do 

Server output to your laptop as an input to use your laptops screen as a monitor??

Why not just set up remote desktop?

But to directly answer your question, what kind of laptop is it? Some have the DVI input and some have it as output only.

---

### Post by mority on 2006-03-09
I prefer server administration through ssh. It is not very wise to install a graphical system like the X server on a server system. Something like remote desktop is overkill for administrating a server.
The shortcoming of ssh being the only way to get a shell in the server is, that if you mess with the network configuration it may happen that you are not able anymore to open a ssh connection. In that case there are basically two ways to get a shell on the server again: The easiest is to plug in a normal VGA display (it may be a really really old one as you just want a shell, so resolution doesn't  matter very much) and a keyboard. The other way is maybe a bit more elegant: Connect with a 9-pin serial cable. For that to work you need a terminal emulator like minicom (Linux) or HyperTerminal (Windows) and a 9-pin serial interface (its called COM port in Windows) of course. And I don't know exactly what has to run on the server side to be able to connect.

---

### Post by MJSOnline on 2006-03-09
Hi Mority.  How do I setup remote access then so I can control the server via the laptop?  What do I need to install on both systems?  The server is curenty my main pc with ubuntu on for desktop use.  Thanks. M

---

### Post by mority on 2006-03-09
[QUOTE=MJSOnline]Hi Mority.  How do I setup remote access then so I can control the server via the laptop?  What do I need to install on both systems?  The server is curenty my main pc with ubuntu on for desktop use.  Thanks. M[/QUOTE]

Well, I don't know if my advise fits your needs but you should consider that running a server is very different from running a desktop system.
On a server system security is an even more important issue than on a desktop system since a server is probably offering services in the internet (like a webserver or mldonkey server). Every service running on a server connected to the internet opens a port to the internet and is therefor a potential security risk. So the rule of thumb is to install only the packages which you really need on a server system since every piece of software is a potential security risk, too.

Considering all this, it is not a very good idea to just take an exisiting desktop system and put it in service as a server. Especially through the default desktop Ubuntu installation many packages get installed which you will never need on a server system. First of all you don't need a desktop environment like GNOME and not even a graphical system like the X server on a server system.

I would recommend you to read some basic documents about networking fundamentals (like the [Linux Network Administrators Guide](http://www.faqs.org/docs/linux_network/), it is a bit outdated and you can skip many sections but it is a good starting point). After this you should reinstall your server machine with the server version of Ubuntu or even Debian. To install the server version of Ubuntu I think you have to enter "server" at the boot prompt of the installation CD.

But to answer your question:
Establishing a ssh connection is pretty easy.

1. Make sure the network configuration of both, the client and the server, are working. Ping the server from the client to confirm this.
```

ping <server_ip>

```

2. Make sure the package "ssh" is installed on both systems.
```

apt-get install ssh

```

3. Open the ssh connection from the client.
```

ssh <user>@<server_ip>

```

---

### Post by MJSOnline on 2006-03-09
Ok. Got all that, I made notes until system is ready, what software do I need to install for a clean installion of the server?  I have a nice clean harddrive for the system and a slave drive for the shares and downloads.  Thanks again. M

---

### Post by mority on 2006-03-10
[QUOTE=MJSOnline]Ok. Got all that, I made notes until system is ready, what software do I need to install for a clean installion of the server?  I have a nice clean harddrive for the system and a slave drive for the shares and downloads.  Thanks again. M[/QUOTE]

I am pretty new to Ubuntu so I can't tell you exactly how to do it with Ubuntu. But I think you have to boot from the normal Ubuntu installation CD and type "server" to the boot prompt right after the CD was booted. That should install a basic server system without graphical environment. SSH should be installed by default. After that you can install the packages you need with apt-get or aptitude. Which packages you need depends on what you are planning to do (for example apache or apache2 as a webserver, proftp or vsftp as a file server, samba as Microsoft windows style file and printer server etc.). For file sharing I would recommend the mldonkey-server package.

---

### Post by MJSOnline on 2006-03-10
Thanks for the reply.  I am going ti use it to download files to via p2p and torrent.  Then use them and the server as a file server for personnel use.  What do I need?  I have two hard drives in there at the mo.  small one as boot and 2nd as slave / mp3, docs etc.  M

---

### Post by mority on 2006-03-10
There are many ways to achieve this. As I said before I would use mldonkey as file sharing client. It is able to connect to many file sharing networks like the edonkey network (used by popular eMule client) and BitTorrent too and it is usable via telnet, web interface or a GUI connecting to the server.

And then you could make available the downloaded files to your home network through a FTP server (e.g. proftp, vsftp), a web server (e.g. apache2), a samba server or all at once. For getting started I would say that a webserver would do it. But you can't delete the files through the webserver, so you would have to login via ssh and delete old downloaded files from time to time. With FTP you could delete and organize the files on the remote server from a local client program.

---

### Post by WildTangent on 2006-03-10
For a fileserver, you just need to set it up with SMB or NFS. SMB is probably better as it offers the widest compatibility. install Samba for SMB networking. For torrent downloading...hmm...myself personally, I use TorrentFlux, which is a web-based client, but it requires you to install Apache, mySQL and PHP, and thus you see this is beginning to get complicated...

-Wild

---

