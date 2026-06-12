---
title: "Many people are having problems with Winmodems - But anyone on laptops?"
date: 2006-09-17
forum: Hardware &amp; Laptops
---

### Post by daller on 2006-09-17
Hi There,

I work in an Electronic-shop in Århus, Denmark

I found a box with 20 brand new winmodems, which I kind of decided to throw out!

But right before I did it, I found a thread on this forum, with a guy who's having a problem with his Winmodem.

Actually, after some searching, it seams that ALOT of people are suffering of bad winmodem support.

The ones I found, was PCMCIA, and therefore mainly for laptops!

Is any laptop-users having problems with their build-in modem (or missing a modem?)

Fact is, I have no idea of how to setup a winmodem, especially not when pcmcia...

How do I find out if the pc has detected it? (no changes in lspci! - But in dmesg!)

lspci:

```

lspci > before
INSERTING THE CARD
lspci > after
diff before after
NO OUTPUT

```

dmesg:

```

[17187704.224000] pccard: PCMCIA card inserted into slot 0
[17187704.224000] pcmcia: registering new device pcmcia0.0

```

Please help me test if ubuntu supports this out-of-the-box, or if it's possible to setup!

If successful, I'll be happy to give these cards to people who need them!

---

### Post by towsonu2003 on 2006-09-18
check out what scanmodem will tell about that modem. you can find out how to run scanmodem from the wiki link in my signature (second link).

---

