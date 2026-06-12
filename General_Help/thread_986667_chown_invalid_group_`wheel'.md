---
title: "chown: invalid group: `:wheel'"
date: 2008-11-18
forum: General Help
---

### Post by bilijoe on 2008-11-18
While trying to install a LightScribe labeler program from the command line, using the command line "**sudo dpkg -i labeler.deb"**, after a screen or so full of normal looking messages, I get about 50 messages reading "chown: invalid group: `:wheel'".  What's up with the group 'wheel'?  What do I need to do to get this software to install? :confused:

---

### Post by ITAndrew on 2008-11-18
The wheel group is a group which limits the number of people who are able to su to root. This usually consists of a group named &#8220;wheel&#8221; and a set of users that are permitted to use the utility &#8217;su&#8217; in order to change to root.

This is not widely used anymore (Ubuntu does not use the wheel group, whereas FreeBSD does).

Kind of wierd that an application packaged for debian would use this call, I will look into it and update as necessary.

Speaking of, where did you get the software? Is it possible to build this application from source?

---

### Post by sisco311 on 2008-11-18
It's just a guess, but you can try to create a group *wheel* and add your user to the group:
```
sudo addgroup wheel
sudo adduser ***username*** wheel
```

---

