---
title: "Can't access class's public server space"
date: 2008-09-23
forum: General Help
---

### Post by Garrulousbrevity on 2008-09-23
This is kind of a silly problem.  for one class, there's a public server space, that in class, on the windows machines, we're told to go to Start - Run and type in an \\*ipaddress* This is the same as typing the ip address into Internet Explorer (No option on those computers unfortunately), or Windows explorer too.

However, I can't do it on my computer because I don't know what protocol it's using. 

I thought it would be WebDAV and Samba, but nothing works when I try using the "Connect to Server" GUI.  

Any help?

---

### Post by fooman on 2008-09-23
isn't it the same as pressing alt-f2 ?

that brings up a run dialog box,  into which you can type an ip address ([http://*ipaddress*](http://*ipaddress*)).  press enter and it will load in your default browser.

for instance, if i press alt-f2,  then type into the box:

```
http://ubuntuforums.org
```

ubuntu forums will open in firefox for me.

---

### Post by Garrulousbrevity on 2008-10-11
Well, it does open a firefox window, but this particular server space doesn't seem to work in firefox.  On the school computers typing the ip address into IE would work, but firefox rarely seems equipped to handle the odd ways my school decides to handle "security" and "ease of access."

---

### Post by Sam on 2008-10-11
> **Garrulousbrevity said:**
> This is kind of a silly problem.  for one class, there's a public server space, that in class, on the windows machines, we're told to go to Start - Run and type in an \\*ipaddress* This is the same as typing the ip address into Internet Explorer (No option on those computers unfortunately), or Windows explorer too.

However, I can't do it on my computer because I don't know what protocol it's using. 

I thought it would be WebDAV and Samba, but nothing works when I try using the "Connect to Server" GUI.  

Any help?

Try in nautilus (location):```
smb://ipaddress
```

---

### Post by Garrulousbrevity on 2008-10-14
Nope.  That just leads to an empty window that stops trying to load anything after a minute or two. 

If it changes anything, this server space is password protected.

---

