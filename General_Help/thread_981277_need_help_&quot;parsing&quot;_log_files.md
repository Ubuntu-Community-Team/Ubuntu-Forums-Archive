---
title: "need help &quot;parsing&quot; log files"
date: 2008-11-13
forum: General Help
---

### Post by anystupidname on 2008-11-13
I'm using conky to display syslog/dmesg/auth.log/etc and (see screenshot) there is too much on each line. I'd like to just strip everything before and including the hostname on each line. Could somebody please help me do this in one of these ways:

-I'm using the tail option in conky but if there is another way that would work better I'm fine with that
-Is there an additional conky option similar to ${offset} that would work here? (plain  offset doesn't work because only the first line is offset)
-can I add a combination of grep/wrap/cut/fold/whatever to the tail command to accomplish what I want?

---

### Post by jamesrl on 2008-11-13
gawk is the command you need (see man gawk).

As a very basic example:
```

cat /var/log/auth.log | gawk  '{ print $5, $6, $7, $8, $9, $10, $11, $12, $13, $14, $15, $16, $17, $18, $19, $20 }'

```
This print the 5th - 20th columns of the auth.log file.

---

### Post by loomsen on 2008-11-13
Yes, you can add multiple pipes.

for instance, lets say i'm searching for a deb pkg i build some time ago in my home dir, lets say cairo-dock, and lets assume also i don't remember if it was 
1)cairo-dock or cairo_dock or maybe even Cairo-Dock, 
further
2) i'm only interested in my .deb packages
3) my source/build folder is in /home
```

foobar@tiffany:~$ locate -i cairo | grep -i dock | grep home | grep amd64 | grep deb
/home/src/cairo-dock-plugins_1.6.3.1-1_amd64.deb
/home/src/cairo-dock-themes_1.6.3.1-1_amd64.deb
/home/src/cairo-dock_1.6.3.1-1_amd64.deb
foobar@tiffany:~$ 

```

Alright, now for some reason I only want the packageversion to be shown, anything else should be omitted. Thanks to the debian policy each deb pkg is named unique, tho always pkgname_ver_arch.deb

So we can take "_" as our delimiter for the cut command
```

foobar@tiffany:~$ locate -i cairo | grep -i dock | grep home | grep amd64 | grep deb | cut -d "_" -f2 | cut -d "_" -f1
1.6.3.1-1
1.6.3.1-1
1.6.3.1-1
foobar@tiffany:~$ 

```

-d specifies the delimiter, in other words where the term should be cut. So our first cut will cut the term at the first occurence of "_" here, and were interested in field 2.

```
/home/src/cairo-dock-plugins  ---cut--- _ ---cut---   1.6.3.1-1_amd64.deb
field 1                                                       field 2

```
Ok, the last cut does the same for 
1.6.3.1-1_amd64.deb
cause thats all we got left by now here. And here we want to keep field 1.

---

### Post by anystupidname on 2008-11-13
@jamesrl: Thank you! It turns out which utility I was using wasn't so much the problem as how I was trying to use them in conky. Using the built-in tail option doesn't allow you to manipulate the output?!? When I switched to using this type of thing instead
> ${execi 1 tail -n 7 /var/log/messages | cut -c22-400}
it worked as I was hoping. gawk and sed are obviously way more powerful than cut and could do what I need as well. I tried and got close to figuring out the complex command that would have done it for me but it was too much for my brain.

@loomsen: I've found a similar method. Thank you anyway though!

---

