---
title: "[SOLVED] unable to resolve host"
date: 2008-08-02
forum: General Help
---

### Post by Racecarandy on 2008-08-02
Hello, i've been trying setup wireless on my laptop and i've been following the guide, but i think i've got a larger problem: any time i type a command into the terminal, i get this:

```
sudo: unable to resolve host roy-laptop
```

:guitar:

---

### Post by Dr Small on 2008-08-02
Please list your /etc/hosts by running:
```
cat /etc/hosts
```

Also, please include your hostname:
```
hostname
```

Dr Small

---

### Post by eldragon on 2008-08-02
for what it worth, make sure this line is in /etc/hosts
```

127.0.1.1 hostname

```
where hostname is your computer's host.

good luck

---

### Post by Racecarandy on 2008-08-02
Thanks for the quick response.  Here is what i've got:
A ```
cat /etc/hosts
```

127.0.0.1 localhost
127.0.1.1 roy-laptop.Belkin

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

B ```
hostname
```

roy-laptop

is all.

---

### Post by jerome1232 on 2008-08-02
instead of 
> 127.0.1.1 roy-laptop.Belkin

it should be
> 127.0.1.1 roy-laptop

But you are going to need sudo access to edit that file.
I guess you will have to boot into recovery mode to edit it, once in recovery mode use nano to edit the file (or vi or vim or whatever)

```
nano /etc/hosts
```

ctrl+x then 'y' then enter will save the file in nano

edit: wow ones really like to hide the dots don't they :)

---

### Post by Racecarandy on 2008-08-02
when i try to login with recovery mode, it tries to fix stuff but it makes me login normally.  i tried to save the file normal but it didn't save.  can't i give the sudo command within terminal?

---

### Post by jerome1232 on 2008-08-02
> **Racecarandy said:**
> when i try to login with recovery mode, it tries to fix stuff but it makes me login normally.  i tried to save the file normal but it didn't save.  can't i give the sudo command within terminal?
when you get into recovery mode it should have the option to use a root terminal. I suggested doing that because I am under the impression that sudo isn't working at all for you (I know hostname stuff can break sudo)

---

### Post by Racecarandy on 2008-08-02
that is true, how do i login as root from there?  i don't know any terminal stuff, i'm a windows "kiddy".

---

### Post by jerome1232 on 2008-08-02
ok step by step this is what you'll need to do.

When you first boot up your computer and it loads grub with all the different OS choices, one down should be blah blah (recovery mode)

If the grub menu doesn't pop up start pounding escape when you see a message like 'Grub loading stage 1.5'

select that hit enter, you should see a bunch of text fly past and you'll end up at a blue screen with a few options.

3rd one down you should have 
root   drop to a root shell   (may not be exact wording but yeah)
select that one and you should be dropped to a prompt that looks like

```
root@roy-laptop:~#
```
go ahead and type in
```
nano /etc/hosts
```
that should bring up something similar to what you saw when you ran cat /etc/hosts earlier.

just change roy-laptop.Belkin to roy-laptop then hit ctrl+x hit 'y' then hit enter. you should be back at your root prompt. just type in **reboot** and let everything happen like normal it should be fixed now

---

### Post by Racecarandy on 2008-08-03
SOLVED.  Thanks.

---

### Post by jerome1232 on 2008-08-03
Glad to help don't forget to mark the thread as solved by clicking on thread tools>>mark as solved (I can never remember exact wording lol) so others will know this thread has a solution. :)

---

