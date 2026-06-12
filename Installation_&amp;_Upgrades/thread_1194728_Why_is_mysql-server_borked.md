---
title: "Why is mysql-server borked?"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by symbiat on 2009-06-23
Hope someone can help because after wasting several hours Im ready to wipe the drive and install a different distro.

Ive been using my Ubuntu box as a development machine for some PHP work. I haven't worked on it for a few months but came back to it recently. Im using MySQL for this work. Anyway, I found my MySQL database wasn't working so I tried to login and my normal password failed. In fact all of my usernames dont work.

After trying various things I thought I would stop and reinstall mysql-server. I tried '/etc/init.d/mysqld stop', that failed. No error message. Nothing in the logs. I ran ps and found the pid and manually killed mysqld.

I used Synaptic to remove all mysql-common, -server and -client packages. I then reinstalled them. The configurations script ran and gave me error about connecting to mysql. There is no init.d script - its gone. I tried this several different ways and have so far been unable to get MySQL running at all. Nothing works! Very frustrating because I dont have time to waste on this stuff, I have work to do!

Whats annoying is that I didn't make any changes to the databases - it just stopped working for no apparent reason.

---

