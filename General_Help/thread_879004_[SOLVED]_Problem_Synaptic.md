---
title: "[SOLVED] Problem Synaptic"
date: 2008-08-03
forum: General Help
---

### Post by Enshin on 2008-08-03
I run in this problem with installing packages.

Couldn't connect to localhost:4001 (127.0.0.1) - (111 Connection refused) 

This was never a problem before.

Can someone tell me what I have to do to fix this.

I tried already
apt-get clean
apt-get upgrade
apt-get update

Same message.

Thanks

---

### Post by drs305 on 2008-08-03
Try System, Preferences, Network Proxy and see if you get the message with Direct Internet Connection selected.

You can also take a look at System, Admin, Network, Hosts to make sure everything looks ok there (no added words to your hostname, etc).

---

### Post by Elfy on 2008-08-03
If that doesn't help have you installed anon-proxy or similar. Seen he same errors here relating to anon-proxy.

---

### Post by Enshin on 2008-08-03
Hello,

Thanks for the quick reply.

/etc/hosts

127.0.0.1	localhost
127.0.1.1	frwi-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


And in Networkproxy: Direct Internet Connection is enabled

I don't see a problem here.

---

### Post by Enshin on 2008-08-03
> **forestpixie said:**
> If that doesn't help have you installed anon-proxy or similar. Seen he same errors here relating to anon-proxy.

That's helping. I have installed anon proxy.

I already got rid of this, as I saw somewhere else something about proxy-problems.

But de-installing didn't solve the problem.

Is there more to fix this?

---

### Post by drs305 on 2008-08-03
If the uninstall did not take care of this:
```
unset http_proxy
```

---

### Post by Enshin on 2008-08-03
> **drs305 said:**
> If the uninstall did not take care of this:
```
unset http_proxy
```

I ran the command as user, but that didn't help.

Must I run this as superuser or not?

I tried with sudo, but the unset command wasn't recognized.

---

### Post by Elfy on 2008-08-03
Purge it if that doesn't help - that seemed to be the way out in the threads I saw. 

But then I didn't see drs305 - suggestion either, nor do I understand it :)

Edit - check in synaptic for residual configs

---

### Post by Enshin on 2008-08-03
> **forestpixie said:**
> Purge it if that doesn't help - that seemed to be the way out in the threads I saw.

But then I didn't see drs305 - suggestion either, nor do I understand it :)

 sudo apt-get purge anon-proxy
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Statusinformatie wordt gelezen... Klaar
Pakket anon-proxy is niet geïnstalleerd, en wordt dus niet verwijderd
De volgende pakketten werden automatisch geïnstalleerd en zijn niet langer nodig:
  libxerces27
Gebruik 'apt-get autoremove' om ze te verwijderen.
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.

Nothing seems to happen, because I removed anon-proxy in an earlier stage.
(when I saw that this might be a proxy-problem)

I don't understand the suggestion of drs305 either, but it makes sense, because I saw that http_proxy was being set during the installation of anon-proxy.

Still I have this problem.

I don't know how to purge something that's already removed. 

Can I do something by hand?

---

### Post by Enshin on 2008-08-03
> **forestpixie said:**
> Purge it if that doesn't help - that seemed to be the way out in the threads I saw. 

But then I didn't see drs305 - suggestion either, nor do I understand it :)

Edit - check in synaptic for residual configs

I almost missed your last line.
How can I check for residual configs in Synaptic?

---

### Post by drs305 on 2008-08-03
The 'unset' command resets an environment variable. Since it changed something it is possible that it was still set for the proxy even though anon-proxy is no longer installed. The other thing that the environment variable may effect is the mode synaptic is started in. Try using 'gksu synaptic' rather than going through the menu. Other than that, I'm out of ideas but will follow along in hopes of learning something. Good luck.

---

### Post by Elfy on 2008-08-03
OPen synaptic and ...

Edit - sorry had to go :)

---

### Post by Enshin on 2008-08-03
> **drs305 said:**
> The 'unset' command resets an environment variable. Since it changed something it is possible that it was still set for the proxy even though anon-proxy is no longer installed. The other thing that the environment variable may effect is the mode synaptic is started in. Try using 'gksu synaptic' rather than going through the menu. Other than that, I'm out of ideas but will follow along in hopes of learning something. Good luck.

Yes.

You last shot, was a golden one drs305. I succesfully installed something (3dchess :lolflag: )

Is there a problem with rights?

I don't have to give my password anymore when using Synaptic.
It clearly needs rootprivileges.
Can I undo this situation? Or do I have to use gksu from now?

---

### Post by Elfy on 2008-08-03
When you use your password for synaptic - it remembers for a while - then will ask again. Wherre there any residuals ?

---

### Post by Enshin on 2008-08-03
> **forestpixie said:**
> OPen synaptic and ...

Edit - sorry had to go :)

Thanks Forestpixie,

If I go there, at the right-top screen the packages are all that I can purge?

So, I have to see anon-proxy there. When I suspect purging that package would solve the problem?

I have a lot of programs there (similar to your picture), but no anon-proxy.

---

### Post by Elfy on 2008-08-03
Did you click residual configs to see them or where there none present - I didn't when I did screenshot and suspect that you're synaptic looks more or less exactly the same as mine :D

---

### Post by Enshin on 2008-08-03
> **forestpixie said:**
> Did you click residual configs to see them or where there none present - I didn't when I did screenshot and suspect that you're synaptic looks more or less exactly the same as mine :D

I click Residual Configs and there was no package selected, as in your screenshot.

---

### Post by Elfy on 2008-08-03
If there were no packages present in the residual config tab then you have none - I have but just haven't got round to getting rid of it.

If you've completely purged anon-proxy and there are no residuals and you've done apt-get purge (which should have done that anyway) and you've done the unset_ command I don't know then.

The only thing I could suggest would be to check there are no folders relating to anon-proxy hidden in your home folder.

---

### Post by Enshin on 2008-08-03
Thanks Drs305 and Forestpixie for your help,

I hit the sack and will be more carefull with installing with synaptic.
It seems very handy, but can bring me in trouble.

I now have a workaround with gksu. May be after a restart this won't be necessary anymore.

Bye.

---

### Post by drs305 on 2008-08-03
There must be some residual setting hanging around. Since root's environment isn't affected by them, take a look in your ~/.bashrc or ~/.bash_profile files. If you don't find anything listing "localhost", you could do a search in your home directory, looking for snippets that might set it:

```

sudo grep -R "localhost:4001" *

```

---

### Post by Enshin on 2008-08-04
> **drs305 said:**
> There must be some residual setting hanging around. Since root's environment isn't affected by them, take a look in your ~/.bashrc or ~/.bash_profile files. If you don't find anything listing "localhost", you could do a search in your home directory, looking for snippets that might set it:

```

sudo grep -R "localhost:4001" *

```

I used  sudo grep -R "localhost:4001" *
It didn't return anything.

Today I started my computer and guess what.
There seems no problem anymore.
=D>

 So:    purge anon-proxy
        unset http_proxy
        reboot

Perhaps in conjunction with the apt-get commands.


Thanks for the help.

---

### Post by Elfy on 2008-08-04
Glad it did it - whichever did do it :d

Could you mark thread as solved please.

---

