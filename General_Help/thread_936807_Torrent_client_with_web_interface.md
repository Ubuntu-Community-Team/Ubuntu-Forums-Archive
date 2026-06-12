---
title: "Torrent client with web interface?"
date: 2008-10-03
forum: General Help
---

### Post by G1ZmO65 on 2008-10-03
Does anyone know if theres a torrent application that I can run on an ubuntu 8.04 server at the cli that also has a web-based interface so that it can be managed remotely?

I can run rtorrent via an ssh connection but I'd prefer a better gui control of it or something like it.

Thanks

Paul

---

### Post by _sAm_ on 2008-10-03
Check out these two:

[http://tf-b4rt.berlios.de/](http://tf-b4rt.berlios.de/)
[http://www.torrentflux.com/screenshots.php](http://www.torrentflux.com/screenshots.php)

---

### Post by itbhp on 2008-10-03
[http://deluge-torrent.org](http://deluge-torrent.org)

Bye,
 Paolo

---

### Post by G1ZmO65 on 2008-10-03
Doesnt look like Deluge can be run from the CLI though Paolo. Or am I wrong?

Thanks Sam, that might be what I need however my ISP doesnt allow me to run a webserver on my home connection on port 80 but maybe I can get round that.

I'll take any other suggestions too :)

Thanks

Paul

---

### Post by aurelieng on 2008-10-03
There is also MLDonkey ([http://mldonkey.sourceforge.net/Main_Page](http://mldonkey.sourceforge.net/Main_Page)), which can handle several protocols, among which bittorrent.

---

### Post by hyper_ch on 2008-10-03
just use rtorrent.. it has some webinterfaces but those are not really needed. rtorrent runs in teh terminal using ncurses... running rtorrent in screen let's you simply de- and reattach the session from anywhere you can use SSH.

---

### Post by itbhp on 2008-10-03
Sorry. :(

Paolo

---

### Post by zvacet on 2008-10-03
Did you tried [Transmission]("http://www.transmissionbt.com/")? maybe is better to install new version from source then one from repos.

---

### Post by AbsolutIggy on 2008-10-03
Azureus (or Vuze as its called now apparently has a web interface aswell: [http://azureus.sourceforge.net/plugin_details.php?plugin=azhtmlwebui](http://azureus.sourceforge.net/plugin_details.php?plugin=azhtmlwebui)

Don't know if you can use it from the command line though..

---

### Post by G1ZmO65 on 2008-10-05
Confused & frustrated again

Why is nothing simple in linux?  Grrr

MLDonkey
I installed mldonkey-server (eventually) using the quickstart guide ([http://mldonkey.sourceforge.net/Quickstart_guide](http://mldonkey.sourceforge.net/Quickstart_guide)) but after the apt-get bit it goes onto initial setup via telnet? Tried that from the ssh session and got stuck in telnet (which didnt connect to mldonkey that I could see) and had to kill the telnet session from another window. :( So couldnt set the admin pass as described.

apparently mlnet is running in the background but cant see how to use it. Tried to connect on port 4080 via browser on local network but nowt. I also cant sudo kill the process id for it either.

```
paul@ubuntu:~$ ps -all
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
0 T  1000 10888 10529  0  80   0 -  6849 -      pts/0    00:00:00 mlnet
0 S  1000 11044 11025  0  80   0 -   803 -      pts/2    00:00:00 telnet
0 R  1000 11045 10906  0  80   0 -   607 -      pts/1    00:00:00 ps
paul@ubuntu:~/downloads$ kill 11044
paul@ubuntu:~/downloads$ telnet
telnet> open 127.0.0.1 4000
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.

quit
close
logout
^[
Terminated  <---- KILLED PROCESS FROM ANOTHER SESSION
paul@ubuntu:~$ ps -all
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
0 T  1000 10888 10529  0  80   0 -  6849 -      pts/0    00:00:00 mlnet
0 R  1000 11048 10906  0  80   0 -   607 -      pts/1    00:00:00 ps
paul@ubuntu:~$ kill 10888
paul@ubuntu:~$ ps -all
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
0 T  1000 10888 10529  0  80   0 -  6849 -      pts/0    00:00:00 mlnet
0 R  1000 11049 10906  0  80   0 -   607 -      pts/1    00:00:00 ps
paul@ubuntu:~$ sudo kill 10888
paul@ubuntu:~$ ps -all
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
0 T  1000 10888 10529  0  80   0 -  6849 -      pts/0    00:00:00 mlnet
0 R  1000 11051 10906  0  80   0 -   607 -      pts/1    00:00:00 ps

```

Torrentflux-b4rt:
Might try this but it means installing and configuring a webserver which is an extra thing I dont really need.

Azureus/Vuze, Deluge: 
No CLI install for these.

Transmission:
Installed transmission-cli but just get "Cannot open display" when I run it and not really sure that this has an interface for managing it remotely by gui.

rtorrent:
Yes, this does work hyper_ch but it's ugly and so I'd prefer if I could manage my downloads through some sort of gui remotely.

---

### Post by hyper_ch on 2008-10-05
what does ugliness has to do with it? I mean it's not like you'll look 24/7 at the ncurses interface ;)

---

### Post by G1ZmO65 on 2008-10-05
ncurses? I'll need to look that one up too. No idea what it is or what it's for but if it's helpful I'll try it.

Had a quick look at: [http://www.gnu.org/software/ncurses/ncurses.html](http://www.gnu.org/software/ncurses/ncurses.html)

but the whole page could be in Chinese for all the sense it makes to me lol

---

### Post by hyper_ch on 2008-10-06
[http://www.mostlygeek.com/wp-content/uploads/2008/06/rtorrent-main.png](http://www.mostlygeek.com/wp-content/uploads/2008/06/rtorrent-main.png)

---

### Post by G1ZmO65 on 2008-10-06
Yes that does look like the rtorrent interface but where does the ncurses thing come into it? Does it help?

---

### Post by hyper_ch on 2008-10-06
that's ncurses what you see there ;)

---

### Post by jerome1232 on 2008-10-06
Was forwarding an X session via ssh not an option? It'll bring the gui to your desktop. However if you lose the connection the program will close.

```
ssh -X user@host "transsmision"
```

---

### Post by G1ZmO65 on 2008-10-07
I dont have a gui on my server jerome1232 so I don't think that'll help (unless I'm misunderstanding you)

hyper_ch: Sorry, I still don't understand. That looks to me like a screenshot of a normal rtorrent session. No?

My problem with rtorrent is not the functionality but the awkwardness of use. Key combinations etc. I'd much prefer if I could manage my torrents remotely via a browser. 

The only real option I can see for this is the Torrentflux-b4rt mentioned previouly which runs via a webserver. I had thought there may be some app which I could connect to on another port to manage the torrents via a gui (not unlike webmin for managing a server where you connect via a secure https session to port 10000)

---

### Post by G1ZmO65 on 2008-10-07
Well, I've also run into problems with torrentflux...

During the install I'm getting: Error: Cannot connect to database. Check username, hostname and password?

Dunno if this is allowed but heres my post on their forum:
```

http://tf-b4rt.berlios.de/forum/index.php/topic,1535.0.html
```

If anyone can supply me with a pointer I'd appreciate it.

Thanks

Paul

---

### Post by czeRozi on 2008-10-08
Hi,
what about [http://code.google.com/p/rtgui/](http://code.google.com/p/rtgui/) ? :)

---

### Post by jerome1232 on 2008-10-08
Here is a screenshot of what transmissions web interface looks like.

---

### Post by G1ZmO65 on 2008-10-14
Well I downloaded phpmyadmin in order to fix the issue with the database connection for the b4rt install but I've now got more problems.

When I connect to the webserver I get:

```
Warning: Unknown: open_basedir restriction in effect. File(/var/www/phpMyAdmin/scripts/setup.php) is not within the allowed path(s): ('') in Unknown on line 0

Warning: Unknown: failed to open stream: Operation not permitted in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/phpMyAdmin/scripts/setup.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
```

Can anyone advise as to what the possible cause of this is? Is it a php issue, apache issue or filesystem?

:confused:

---

### Post by Archmage on 2008-10-14
Did you try rtorrent with the graphical interface? It looks nice.

---

### Post by G1ZmO65 on 2008-10-14
Not yet as it looks like I need to configure apache and php for yet another module (XML-RPC) and tbh I don't even know whether my php/apache installation is working or not.

I'm sure if I can get the above working properly then getting the gui for rtorrent or b4rt should be a breeze (lol)

It's all very confusing :(

---

### Post by G1ZmO65 on 2008-10-18
Ok well after all that I have gone back and configured rtorrent using it's directory watch facility so that I can just drop torrents into a folder and have them downloaded automatically. Still don't really like the interface but it's much simpler than the configuration of the alternatives.

You win hyper_ch :)

Thanks for the advice folks!

Paul

---

### Post by maxadamo on 2010-02-15
it's a old thread... anyway: I wanted to say you can use either deluge or azureus thru a SSH tunnel, having installed the interface on the remote computer.

---

