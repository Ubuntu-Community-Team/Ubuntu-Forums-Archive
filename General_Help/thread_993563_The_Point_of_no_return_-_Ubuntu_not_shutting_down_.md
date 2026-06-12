---
title: "The Point of no return - Ubuntu not shutting down or restarting"
date: 2008-11-25
forum: General Help
---

### Post by b3n0 on 2008-11-25
Hey all,
For about 3 days I've had this odd problem. When I select shutdown or restart the OS disappears, the ubuntu logo appears with the loading bar, text flys ups the screen. Really just like any normal shutdown sequence. However at the point where the machine needs to turn itself off, it stops following the sequence. At this point its just a black screen. I usually have to hold the power button in to turn it off.
Any ideas?
Thanks in advanced.

Edit: 27Nov08
Thanks to poebae,
this is the solution that worked for me
```
sudo gedit /etc/modules
```
add the following line to the text
```
apm power_off=1
```
Give it a couple of restarts if it doesn't straight away.

Thanks

---

### Post by decard_pain on 2008-11-25
i've seen this with 8.10 on and old pc myself..i have so far found no fix for it

i can even hear the hard drive power itself off.

---

### Post by b3n0 on 2008-11-25
> **decard_pain said:**
> i've seen this with 8.10 on and old pc myself..i have so far found no fix for it

i can even hear the hard drive power itself off.
Mines a rather new lappy

---

### Post by poebae on 2008-11-25
What happens if you use 

```
sudo halt
```

instead of the regular shutdown option? I was having a similar problem and "sudo halt" would correctly shut down my system.

I fixed it by adding the following line to my /etc/modules:

```
apm power_off=1
```

Good luck!

---

### Post by jason.b.c on 2008-11-25
> **b3n0 said:**
> Mines a rather new lappy

WOW ..! that really helps this guy alot man.....


i hate this kind of sh*t , a person joins this forum ( i'm refering to myself here as well ) asking for help , and this is the kind of help that he ( myself ) gets...!...?

what a load of crap...

---

### Post by b3n0 on 2008-11-25
> **jason.b.c said:**
> WOW ..! that really helps this guy alot man.....


i hate this kind of sh*t , a person joins this forum ( i'm refering to myself here as well ) asking for help , and this is the kind of help of help that he ( myself ) gets...!...?

what a load of crap...

Gee sorry mate I happened to be away from my laptop. I posted the last post on my blackberry. I got my laptop in October 2007, it a HP DV6000 running intrepid

---

### Post by poebae on 2008-11-25
> **jason.b.c said:**
> WOW ..! that really helps this guy alot man.....

i hate this kind of sh*t , a person joins this forum ( i'm refering to myself here as well ) asking for help , and this is the kind of help that he ( myself ) gets...!...?

what a load of crap...
Huh? I'm utterly confused. 

The person who posted "Mine's a rather new lappy" is the original poster of this thread....

---

### Post by b3n0 on 2008-11-25
> **poebae said:**
> Huh? I'm utterly confused. 

The person who posted "Mine's a rather new lappy" is the original poster of this thread....

I'm confused too, was he trying to help?
BTW
```
sudo halt
```
Works so I'll try that edit you mentioned

---

### Post by b3n0 on 2008-11-25
> **poebae said:**
> What happens if you use 

```
sudo halt
```

instead of the regular shutdown option? I was having a similar problem and "sudo halt" would correctly shut down my system.

I fixed it by adding the following line to my /etc/modules:

```
apm power_off=1
```

Good luck!

At first it was saying that I don't have the permission to save it.
Then I got smart and did this
```
cd /etc
sudo gedit modules
```
I then added the code and it saved.

---

### Post by jason.b.c on 2008-11-25
oops , i hit the reply button on the wrong person...


sorry - nevermind...

---

### Post by poebae on 2008-11-25
> **b3n0 said:**
> At first it was saying that I don't have the permission to save it.
Then I got smart and did this
```
cd /etc
sudo gedit modules
```
I then added the code and it saved.
Cool :)

The easiest way would be to type

```
sudo gedit /etc/modules
```

;)

Let me know how it goes!

---

### Post by b3n0 on 2008-11-25
Blast! No joy sorry. It still wont shutdown properly. Any other ideas?

---

### Post by poebae on 2008-11-26
As far as I know, that solution doesn't work on first shutdown. I know this sounds very Windows-esque, but Try rebooting and see if it works after that.

---

### Post by b3n0 on 2008-11-26
:D Completely agree 'Windows-esque' but believe it or not after one or two resets it has self-repaired. :D
Thanks for your help.

---

