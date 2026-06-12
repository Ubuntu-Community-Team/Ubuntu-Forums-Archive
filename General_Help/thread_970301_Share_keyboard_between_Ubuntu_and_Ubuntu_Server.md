---
title: "Share keyboard between Ubuntu and Ubuntu Server"
date: 2008-11-04
forum: General Help
---

### Post by moncojhr on 2008-11-04
Hello, i've got a Ubuntu Desktop System and a Ubuntu Server System and id like to be able to share my keyboard between them, both have their own monitors.

What would be the best way to do that?

---

### Post by lenswipe on 2008-11-04
> **moncojhr said:**
> Hello, i've got a Ubuntu Desktop System and a Ubuntu Server System and id like to be able to share my keyboard between them, both have their own monitors.

What would be the best way to do that?

Use a KVM switch, i got one off [dabs.com]("http://www.dabs.com") for mere buttons :)

---

### Post by moncojhr on 2008-11-04
Ooh i should have said that id prefer it to be software based, i dont really want to buy a KVM switch...

---

### Post by Peter09 on 2008-11-04
Why not run yur server headless and use your desktop with dual monitors :p

Use FreeNX, it will give you a real remote desktop with no problems.

---

### Post by moncojhr on 2008-11-04
I already have dual monitors for my Desktop machine, and it only has 2 DVI ports so i cant use the other monitor :-(

---

### Post by Peter09 on 2008-11-04
Well using NxFree (or a similar product) will do what you want. As NxFree presents as a window you can move it to one monitor for your servers GUI  and use the other as normal. (as an example)

---

### Post by moncojhr on 2008-11-04
Ahh no what i ment was, i have 3 monitors... and i cant use my 3rd monitor on my Desktop machine (only two DVI ports)

I pretty much want what synergy does except that i dont want to run X on my server machine

Also i dont want to buy a KVM switch...

---

### Post by Peter09 on 2008-11-04
Did not make myself clear. FreeNx shows the remote machine in a window on the client. So you can move that window wherever you want. If you a dual monitors you could drag the window onto one of them - thats all I was saying.

Unfortunately you will still have a spare monitor :p

---

### Post by Peter09 on 2008-11-04
If you do not want to run X its even easier. Install openssh-server on the server machine. Its in the repositories.

Once done you can type in a terminal on your client

```
ssh -X <your user name>@<your servername> xterm
```

this will, after asking for a password, bring up a terminal on you client which is actually running on your server.

You can run any application by substituting xterm for something else.

---

### Post by moncojhr on 2008-11-04
Hrmmm, i already use SSH...

I want to utilize my 3rd monitor...

---

### Post by Peter09 on 2008-11-04
Can you set it horizontal - might make a good coffee table :p

---

### Post by moncojhr on 2008-11-04
Haha, thats not really what i had in mind

If their is no good way to do this ill put X on my server and run synergy :-(

---

### Post by Peter09 on 2008-11-04
In the end you need to decide what you want to do - you most probably do not need your third terminal - but if you are attached to it then the technical solution is secondary.:grin:

---

