---
title: "[SOLVED] Bash: sending commands into a process"
date: 2008-08-18
forum: General Help
---

### Post by WallyWest on 2008-08-18
Hello,
I was wondering how to send information from script into a telnet session.
In the script i have opened a telnet session with an IP and am then prompted to enter the username and psswd. I would like the script to do that for me. Would the same solution for this also work for creating a dialog box of switch commands inside the same telnet session?
THanks,

T.H.

---

### Post by sdennie on 2008-08-18
You may want to look at the expect program:

```

sudo apt-get install expect

```

Then:

```

man expect

```

---

### Post by WallyWest on 2008-08-18
This seems very helpful and pertinent. It will take me a while to go through this because I just started using linux a few weeks ago and these are some of my first encounters with scripting and the bourne type shells. I will keep the thread open in case I have any general questions over the next few days if you don't mind. 
THanks,

T.H.

---

### Post by WallyWest on 2008-08-19
Hello,
can someone tell me what I'm doing wrong with expect here?

[CENTER]#!/bin/bash
gnome-terminal -e "telnet 192.168.118.13" &
expect "username:"
send "manager\r"
expect "password:"
send "*****\r[/CENTER]

The new window spawns and successfully connects to telnet. However nothing after the ampersand seems to work. Here is the error:

[CENTER]tim@tim-desktop:~/Documents$ ./inside_test 
couldn't read file "username:": no such file or directory
./inside_test: line 4: send: command not found
couldn't read file "password:": no such file or directory
./inside_test: line 6: send: command not found
couldn't read file "%": no such file or directory
[/CENTER]

THanks for the help

---

### Post by sdennie on 2008-08-20
I don't think you are using expect correctly.  Have a look at this example: [http://www.osix.net/modules/article/?id=30](http://www.osix.net/modules/article/?id=30).  Essentially, you create an script with expect as the interpreter.  Then, you would run that script as the argument to gnome-terminal.

---

### Post by WallyWest on 2008-08-20
Ok, Ill check that out.
sorry for asking so many basic questions... I'm trying to learn as much as i can on my own but its tough only having google. hopefully ill be able to find a class about this next semester though:)

---

### Post by sdennie on 2008-08-20
> **WallyWest said:**
> 
sorry for asking so many basic questions...

If people didn't ask questions there would be no forums.  :)

---

