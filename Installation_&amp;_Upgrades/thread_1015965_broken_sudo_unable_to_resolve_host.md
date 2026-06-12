---
title: "broken sudo: unable to resolve host"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by redshirtph on 2008-12-19
OK, I've seen other posts on this, but this is different. sudo returns the above error.

hostname is set correct (epesitst); hosts shows 127.0.0.1 epesitst.domainnamestuff

sudo nano -w hosts yields the error

gksu ... needs root password (my password does not get in)

changing the hosts file via System-Administration-Network does not stick.

I'm stuck.

-r

---

### Post by taurus on 2008-12-19
Can you post the outputs of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
cat /etc/hostname
cat /etc/hosts
```

Basically, the /etc/hostname should be the same name that you have in /etc/hosts.

---

### Post by redshirtph on 2008-12-19
cat /etc/hostname

epesitst

cat /etc/hosts

127.0.0.1 epesitst.editout

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by taurus on 2008-12-19
> **redshirtph said:**
> cat /etc/hostname

epesitst

cat /etc/hosts

127.0.0.1 epesitst**[COLOR="Blue"].editout[/COLOR]**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Boot your machine into recovery mode (since you can't use sudo right now) and at the prompt, edit /etc/host

```
nano -B /etc/hosts
```
and change the first line from

```

127.0.0.1 epesitst.editout

```
to look like these.

```

127.0.0.1 localhost
127.0.1.1 epesitst

```
Save it with <Ctrl>x and Y to the question.  Reboot your machine.

```
shutdown -r now
```

---

### Post by stderr on 2008-12-19
And therein lies your answer - remove .editout from the end of your 127.0.0.1 entry in /etc/hosts. It's trying to use 'editout' as a domain name, which is clearly wrong ;)

edit: beaten to it :p

---

### Post by redshirtph on 2008-12-19
Thank you for the help!

It's too bad you can even get into this state with the setup to begin with... something is amiss. I'll give recovery a try.

-r

---

### Post by redshirtph on 2008-12-19
This worked. TY

---

