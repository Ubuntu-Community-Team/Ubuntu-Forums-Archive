---
title: "[SOLVED] Store SSH Locations"
date: 2008-10-25
forum: General Help
---

### Post by opticyclic on 2008-10-25
If I was in Windows, I would use PuTTY to connect to the necessary servers.
In Linux, I am using the Gnome Terminal and the ssh command.

The obvious benefit with PuTTY is that I can store all my frequently used locations by common name and I don't have to remember the IP.
How can I do this in Linux?

---

### Post by cantormath on 2008-10-25
you can predefine short nicknames for Ips that you ssh to in /etc/hosts
    IPAddress     Hostname             Alias
           208.164.186.1        deep.openna.com         nickname1
           208.164.186.2        mail.openna.com         nickname2
           208.164.186.3        web.openna.com         nickname3

$ ssh nickname
           

 or do something like this
[http://articles.techrepublic.com.com/5100-10878_11-6155832.html?tag=rbxccnbtr1](http://articles.techrepublic.com.com/5100-10878_11-6155832.html?tag=rbxccnbtr1)

or if you are at your house, you may be able to define host names for Local Ips for the LAN.  I do this by re-flashing my router with something like Tomato or DD-WRT

---

### Post by Dr Small on 2008-10-25
You can create simple aliases to use in the terminal, to automatically connect to the destination.

First, enable aliases by editing ~/.bashrc and find these lines:
```
#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi
```

Uncomment them, and save it. Now create a new file called .bash_aliases in your $HOME directory, and this is where we will store our aliases. Here is a few examples of aliases you can make, which should help get you started:
```
alias mycroft="ssh 192.168.0.70"
alias maymith="ssh 192.168.0.101"
alias :q="exit"
```

Now, either logout, or run:
```
. .bashrc
```

And your aliases will be loaded. Now you can run your alias in the terminal, just by running:
```
mycroft
```

And it will actually be running:
```
ssh 192.168.0.70
```

But you won't have to type it :D

---

