---
title: "[SOLVED] interesting problem with the fortune command"
date: 2008-08-16
forum: General Help
---

### Post by jmd9qs on 2008-08-16
just recently i found out about the fortune command...kinda fun to mess around with while waiting for downloads. however, when i run fortune as super-user, it says 'command not found'; then if i try #fortune -o (to try and get an offensive fortune), it says 'no fortunes found'... 

do i have to try and enable offensive fortunes somehow? why won't it let me run it as root?

---

### Post by angry_johnnie on 2008-08-16
Superuser **can** run the command, but not with sudo.  Try sudo su instead, and then type exit and enter, to go back to your regular user, which is the most advisable thing to do anyway.

As for the offensive fortunes :p

if you

```
sudo aptitude search fortunes | grep offensive
```

you'll see the result is **fortunes-off** (I just thought aptitude would be faster and more efficient at something like this, than synaptic).

So, what you do is

```
sudo apt-get install fortunes-off
```

and then fortune -o will work as expected. :-)

---

### Post by Vivaldi Gloria on 2008-08-16
> **jmd9qs said:**
> why won't it let me run it as root?

Because 

```
/usr/games
```

is not in root's path. Either add it to root's path or call it as follows:

```
/usr/games/fortune
```

---

### Post by go_beep_yourself on 2008-09-17
fortune -ao

---

### Post by mb_webguy on 2008-09-17
> **go_beep_yourself said:**
> fortune -ao

"fortune -ao" does the same as "fortune -a", since the "-a" options says to pick from all lists, offensive or not.

---

