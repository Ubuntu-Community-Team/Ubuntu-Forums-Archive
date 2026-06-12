---
title: "Packard Bell Grafite"
date: 2009-09-12
forum: Hardware
---

### Post by dmalcomd on 2009-09-12
This external box offer two interfaces, usb and ethernet.
The ethernet interface works under windows with some kind of proprietary driver but i want to use it under linux.
I haven't any idea how to mount this disk under ubuntu.
I tried smbclient and nfs but no success.
Then nmapped the hard disk ip:

```
PORT     STATE SERVICE VERSION
80/tcp   open  http?
4660/tcp open  mosmig?
```

Telnet on port 80 return just a blank page

```
Trying 192.168.1.23...
Connected to 192.168.1.23.
Escape character is '^]'.
?
HTTP/1.0 200 OK
Cache-control: no-cache
Connection: Close

<html>
<head>

</body>
</html>
Connection closed by foreign host.
```

On port 4660...
```
helvete:/home/malcom# telnet
telnet> o
(to) 192.168.1.23 4660
Trying 192.168.1.23...
Connected to 192.168.1.23.
Escape character is '^]'.
helo
?
ARGH!
-_-"

^]
telnet>
```

Any clues?

P.S Under windows the disk is mounted via usb (over ethernet i think)

---

