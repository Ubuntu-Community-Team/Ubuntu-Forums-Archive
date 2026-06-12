---
title: "What does this command do?"
date: 2008-08-26
forum: General Help
---

### Post by shamusl on 2008-08-26
hping3 208.76.217.20 -p 80 -i u30000 -S -A --fast

Or - more specifically, can anybody break this command down for me? I know what the goal of this command is (to ping a site), I just don't know what each string on numbers and letters actually do, by themselves.

---

### Post by Dr Small on 2008-08-26
I don't have hping3 installed, but since you do, you can read the man page by running:
```
man hping3
```

And read each option over and figure out what it does.

---

### Post by doas777 on 2008-08-26
well heres the man page for the app 'Hping3'

[http://linux.die.net/man/8/hping3](http://linux.die.net/man/8/hping3)

208.76.217.20 is the remote IP.

the -p is your TCP port number (80 => http)
the -i is your interval between pings in microseconds 1000000 => 1 second. 
the -S turns on the SYN flag 
the -A turns on teh Ack flag

(a SYN-ACK packet is not supposed to happen at the start of a new connection, but part of an existing one. it goes SYN, ACK, SYN-ACK, SYN-ACK, ...... FIN)

--fast is shorthand for -i u10000 (.1 seconds).

hope that helps,
frank

---

### Post by wirelessmonkey on 2008-08-26
Quickly, it says 
run hping3 against 208.76.217.20, on destination port 80, wait 30000microseconds between pings, sets the SYN and ACK flags.  The --fast is an alias for u10000, and conflicts with "-i u30000".

---

### Post by furialis on 2008-08-26
Trolling /b/ just download it and look at the options by typing

hping3 -help

---

