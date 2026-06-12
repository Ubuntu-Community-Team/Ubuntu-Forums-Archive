---
title: "Don't know password for accessing the terminal"
date: 2008-09-09
forum: General Help
---

### Post by tswann on 2008-09-09
I've been trying to install XAMPP so I can then install Joomla!  I'm trying to follow the instructions on one of the tutorial sites which seems pretty helpful except for the fact that I can't get past step one.

It asks me to type in 'su' on the terminal and then carry out a series of commands.  The problem is that when I type 'su' and hit enter, I get asked for a password.  My normal admin password doesn't work though, and I can't think what password it's talking about.

I hope someone can help me with this.  I've tried on the Joomla! forum but haven't got any reply yet.

---

### Post by iaculallad on 2008-09-09
When using su, you are to input your own user password. Take note that it won't echo any character if you are to input your password.

---

### Post by insanity54 on 2008-09-09
With Ubuntu, you don't need to use su. Instead use sudo.


In fact, I would suggest that you don't use su. su switches you to the root user so you have privileges to do whatever you want with your system files. This is not necessary nor entirely safe. sudo will give you the privileges temporarily, and that's all you need.

example:

Tutorial says:

switch to root

```
$ su
```

run lots of commands

```
$ install joomla yay yay
$ install cool explosion theme pack
$ install plugins
```

Instead of switching to root (su) doing it that way, you can do it this way:

```
$ **sudo** install joomla yay yay
$ **sudo** install cool explosion theme pack
$ **sudo** install plugins
```

(The first time you run sudo, it will ask for your password. This is the same password that you use to log in. You don't have to re-type your password every time you use sudo, as it will last for ~15 minutes)

This way is safer, and is the ubuntu way of using root privileges!

Hope that helps

---

### Post by iaculallad on 2008-09-09
> **insanity54 said:**
> With Ubuntu, you don't need to use su. Instead use sudo.


In fact, I would suggest that you don't use su. su switches you to the root user so you have privileges to do whatever you want with your system files. This is not necessary nor entirely safe. sudo will give you the privileges temporarily, and that's all you need.

example:

Tutorial says:

switch to root

```
$ su
```

run lots of commands

```
$ install joomla yay yay
$ install cool explosion theme pack
$ install plugins
```

Instead of switching to root (su) doing it that way, you can do it this way:

```
$ **sudo** install joomla yay yay
$ **sudo** install cool explosion theme pack
$ **sudo** install plugins
```

(The first time you run sudo, it will ask for your password. This is the same password that you use to log in. You don't have to re-type your password every time you use sudo, as it will last for ~15 minutes)

This way is safer, and is the ubuntu way of using root privileges!

Hope that helps

The right command for installation (either using apt-get or aptitude) would  be:

```
sudo apt-get install application_name
sudo aptitude install application_name
```

And either way, you could use:

```
sudo -i
```

To get to root terminal.

EDIT: If you're on to open system, you could clear your sudo password by typing:

```
sudo -k
```

---

### Post by insanity54 on 2008-09-09
> **iaculallad said:**
> The right command for installation (either using apt-get or aptitude) would  be:

```
sudo apt-get install application_name
sudo aptitude install application_name
```


Yessir, That is the correct command indeed!

I was having some fun with the "install joomla yay yay" but I see that it isn't helping anyone!

---

