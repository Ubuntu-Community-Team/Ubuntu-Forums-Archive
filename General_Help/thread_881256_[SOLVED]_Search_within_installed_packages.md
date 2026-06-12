---
title: "[SOLVED] Search within installed packages"
date: 2008-08-05
forum: General Help
---

### Post by vnetha on 2008-08-05
Hi,

I've been using Ubuntu for a while now and have v7.10 (Gutsy Gibbon) on of my machines - a Compaq Presario v2630US.

I knew of a command a while back that would allow me to search within installed packages for a certain package. I don't remember it however.

I'm not talking about:

```
apt-cache search <string>
``` [searches all packages]

or

```
dpkg -S <string>
``` [shows the path where every single file is installed]

If anyone is aware of something more specific, I would really appreciate the help.


thanks,
Vivek.

---

### Post by spiderbatdad on 2008-08-05
```
$ dpkg-query -l 'build-essential*'
```

```
$ dpkg-query -W -f='${Status} ${Version}\n' build-essential
```

---

### Post by vnetha on 2008-08-06
I get the same response with both commands: 

No packages found matching build-essential.

any other ideas?

Vivek.

---

### Post by Moridin333 on 2008-08-06
sudo aptitude show

or if you are looking for something specific you can use pipes.

sudo aptitude show <package name> | grep <package name>

---

### Post by jerome1232 on 2008-08-06
I think this will do it for ya

```
dpkg --get-selections
```

it gives a list that looks like this
> 
xterm						install
xulrunner-1.9					install
xulrunner-1.9-gnome-support			install
xutils						install
xutils-dev					install
yelp						install
zenity						install
zip						install
zlib1g						install


if you are looking for something specific just pipe it to grep

```
dpkg --get-selections | grep [pattern]
```

edit: Wow, I really left this open for more than 44 minutes watching tv and glancing over man pages there wasn't a post above before

---

### Post by spiderbatdad on 2008-08-06
> **vnetha said:**
> I get the same response with both commands: 

No packages found matching build-essential.

any other ideas?

Vivek.

Then you haven't installed build-essential. Your post is very unclear. 
You asked: > to search within installed packages for a certain package. If you replace build-essential with "a certain package" name, you would get info on that package.

If you want to see all installed packages...you already know how to do that.

---

### Post by vnetha on 2008-08-10
Thanks a lot, guys...

each of your methods worked.

I personally like ```
dpkg --get-selections
``` best,
but the other ways seem to get the job done too.


Vivek.

---

