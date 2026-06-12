---
title: "Transmission config file?"
date: 2008-08-16
forum: General Help
---

### Post by eival on 2008-08-16
i tried looking around the file system but i couldnt find one.

basically i want to know if theres hidden settings that arent availible on the application's Edit > Preferences tab.

what im ultimatly trying to find out is if i can set it to stop seeding/remove the torrent once its finished downloading.


if theres a terminal code(s) that will let me set this ill accept that aswell.

thanks

---

### Post by Vivaldi Gloria on 2008-08-16
> **eival said:**
> Transmission config file?

Look in

```
~/.transmission/gtk
```

---

### Post by thestig_992 on 2008-08-16
Theres no hidden settings for transmission, its pretty basic as far as customisation is concerned

---

### Post by przemo28765 on 2008-10-16
/home/xxx/.config/transmission

---

### Post by Dark9204 on 2008-10-16
Dude, if you download a torrent you MUST upload at least 1.0 Ratio! If nobody seeds , then nobody can download!
So if you dont like seeding, then stay off torrents! In fact, you should stay off all kinds of p2p networks. Becouse they build on that you seed so others can download.

---

### Post by efrenefren on 2009-01-31
> **przemo28765 said:**
> /home/xxx/.config/transmission
this is the correct one. :)

---

### Post by Danyhenriquez on 2010-10-16
I would like te renew this topic with a question that i assume is regarding the config file. I am just experimenting with ubuntu server for a week so my apoligies for the n00b factor.

I want to setup a command line server with ubuntu 10.10. I have installed transmission with the following commands.

Sudo apt-get install transmission-cli
sudo apt-get install transmission-daemon

Now i want to connect to the web interface and it gives me the following notification in my browser : 

403: Forbidden

Unauthorized IP Address.

Either disable the IP address whitelist or add your address to it.

If you're editing settings.json, see the 'rpc-whitelist' and 'rpc-whitelist-enabled' entries.

If you're still using ACLs, use a whitelist instead. See the transmission-daemon manpage for details.


If i try to find settings.json with the command "locate setting.json" executed from my root dir then nothing shows up.

Is there a config file that i can adjust to make this notification dissapear?

If so, where is the config file?

How do i change the transmission user so it starts as user "transmission"?

Thank you in advance




Update : I have found the settings.json file after installing "sudo apt-get install transmission"

Then did a reboot. The settings.json is now located in /etc/transmission-daemon and /var/lib/transmsision-daemon/info/settings.json (had to chmod 775 the info dir). Found this info on the transmission website. 

The settings.json files are empty.

Does anyone know what the problem is?

---

### Post by lilrabbit129 on 2010-10-17
I was actually running into the same issue just now. Here's how I fixed it.

You need to stop the daemon first. If you don't Transmission will OVERWRITE the settings when its stopped ( according to the readme). 

```
sudo /etc/init.d/transmission-daemon stop
```

Then you can edit the settings in /etc/transmission-daemon.

If you try to edit and its blank, its because your current user doesn't have read privileges. I usually just sudo to get around this. For example:

```
sudo emacs -nw settings.json
``` 

Restart the daemon and you should be good to go. 

You may want to change the transmission webui login name and password. Its

```
rpc-username and rpc-password
```

Hope that helps. 

> **Danyhenriquez said:**
> I would like te renew this topic with a question that i assume is regarding the config file. I am just experimenting with ubuntu server for a week so my apoligies for the n00b factor.

I want to setup a command line server with ubuntu 10.10. I have installed transmission with the following commands.

Sudo apt-get install transmission-cli
sudo apt-get install transmission-daemon

Now i want to connect to the web interface and it gives me the following notification in my browser : 

403: Forbidden

Unauthorized IP Address.

Either disable the IP address whitelist or add your address to it.

If you're editing settings.json, see the 'rpc-whitelist' and 'rpc-whitelist-enabled' entries.

If you're still using ACLs, use a whitelist instead. See the transmission-daemon manpage for details.


If i try to find settings.json with the command "locate setting.json" executed from my root dir then nothing shows up.

Is there a config file that i can adjust to make this notification dissapear?

If so, where is the config file?

How do i change the transmission user so it starts as user "transmission"?

Thank you in advance




Update : I have found the settings.json file after installing "sudo apt-get install transmission"

Then did a reboot. The settings.json is now located in /etc/transmission-daemon and /var/lib/transmsision-daemon/info/settings.json (had to chmod 775 the info dir). Found this info on the transmission website. 

The settings.json files are empty.

Does anyone know what the problem is?

---

