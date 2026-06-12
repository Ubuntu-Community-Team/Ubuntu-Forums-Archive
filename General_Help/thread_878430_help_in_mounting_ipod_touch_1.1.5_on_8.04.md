---
title: "help in mounting ipod touch 1.1.5 on 8.04"
date: 2008-08-02
forum: General Help
---

### Post by sinmantky on 2008-08-02
Hi all

Need help mounting ipod touch (1.1.5) onto ubuntu 8.04 (is up-to-date as od Aug 3rd 2008)

Here is what I did:

[LIST=1]
[*] mounted iPod onto a vista w/ iTunes 7.7.1 and backed it up
[*] jailbroke the iTouch on Vista using ziphone 3.0
[*] installed openSSH and BSD subsystem as instructed on [**this**]("https://help.ubuntu.com/community/PortableDevices/iPhone") page
[*] installed ipod-convenience, gtkpod and amarok as in the page above
[*] connected the iTouch to ubuntu
[*] from the terminal, I typed ```
ipod-touch-mount
```
[*] Then i got the following ```

ping: unknown host ipod
iPod is not responding to pings at ipod
Please set the environment variable IGNOREPING if you want to ignore this.
```
[/LIST]

FYI, ubuntu did not recognize the ipod when i connected it (no icons appeared on the dekstop).

I am guessing ubuntu does not recognize the ipod... any help?

---

### Post by K2712 on 2008-08-02
Try:

```
dmesg
```

and check the last few lines to see if the kernel sees the Ipod or not.

---

### Post by sinmantky on 2008-08-02
hi K2712

tried it, gave me more than a hundred log lines. Is there anyway i can filter/narrow it down?
Looked for ipod/apple strings, but couldnt see any (at least in the 80 or so messages that was viewable)

thanks

---

### Post by Nepherte on 2008-08-03
Did it already generate the Firewire GUID? I get that error in 7. too once in a while, but retrying the ipod-touch-mount command works for me. It's most likely you have a weak wifi signal.

---

### Post by Tom--d on 2008-08-03
> **sinmantky said:**
> hi K2712

tried it, gave me more than a hundred log lines. Is there anyway i can filter/narrow it down?
Looked for ipod/apple strings, but couldnt see any (at least in the 80 or so messages that was viewable)

thanks

dmesg | grep "ipod"

try that. mess around with the ipod bit.

---

