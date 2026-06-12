---
title: "Nut - /dev/ttyS0 is locked by another process"
date: 2009-08-21
forum: Hardware
---

### Post by oddwareso on 2009-08-21
I am new to Gnu/linux and have managed to stumble my way through setting up a server.
I am attempting to setup a ups (Ablerex, Not sure what model).

I am using nut and i cannot get it to connect because the ups appears to be in use.
I have these settings in */etc/nut/ups.conf*

[I] [powerpal]
       driver = megatec
       port = /dev/ttyS0
       desc = "Web server"
[/I]

When i run *sudo upsdrvctl start* it returns

  [I]Network UPS Tools - UPS driver controller 2.4.1
  Network UPS Tools - Megatec protocol driver 1.6 (2.4.1)
  /dev/ttyS0 is locked by another processt 
  Driver failed to start (exit status=1)
[/I]
i have searched for ages trying to find out what is using the port but i am not sure where to go. i attempted *ps -ef |grep tty* and it returns

  [I]root      4272     1  0 21:04 tty4     00:00:00 /sbin/getty 38400 tty4
  root      4273     1  0 21:04 tty5     00:00:00 /sbin/getty 38400 tty5
  root      4277     1  0 21:04 tty2     00:00:00 /sbin/getty 38400 tty2
  root      4279     1  0 21:04 tty3     00:00:00 /sbin/getty 38400 tty3
  root      4280     1  0 21:04 tty6     00:00:00 /sbin/getty 38400 tty6
  root      5231     1  0 21:04 tty1     00:00:00 /sbin/getty 38400 tty1
  oddware  14193  5398  0 22:00 pts/0    00:00:00 grep tty
[/I]
but as i am still learning i am not exactly sure what i am looking at but i dont see anything pointing to ttyS0

Does anyone have a suggestion?

Thanks :)

---

