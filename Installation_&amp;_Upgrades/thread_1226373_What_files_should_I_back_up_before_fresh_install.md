---
title: "What files should I back up before fresh install?"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by Lye on 2009-07-29
Well, the title says it. I'm currently running a web server and I'm looking to upgrade my broken and outdated version of Ubuntu 2.6.22-14-server. The tricky part is I'm the second person managing this server so I don't know what configs were changed under the initial installation. My goal is to back up the necessary files and reinstate them on the new server for as seamless of a transition as possible.

I want to keep all user accounts as is. I assume I'll need /etc/passwd and /etc/shadow. Anything else?

I want to keep the web server configs, files. I know to back up /etc/apache2/ and /etc/mysql/ and my web directories(/var/www).

My user directories: /home/

I want to keep my static IP settings. I know to get /etc/network/interfaces. Anything else?

The server doesn't run a DNS server but should I back up any files to keep it's subdomain name?

That's all I can think of at the moment. Can anyone else come up with other important files?

Also, will there be any conflicts with simply replacing these files on the new server?

Thank you for working through this with me! :)

---

### Post by ZaHACKieL on 2009-07-29
Well, you can do a list of all the installed packages with this command:

dpkg &#8211;get-selections | grep -v deinstall > ubuntu-files

I found that here:

[http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)

---

### Post by slakkie on 2009-07-31
> **Lye said:**
> Well, the title says it. I'm currently running a web server and I'm looking to upgrade my broken and outdated version of Ubuntu 2.6.22-14-server. The tricky part is I'm the second person managing this server so I don't know what configs were changed under the initial installation. My goal is to back up the necessary files and reinstate them on the new server for as seamless of a transition as possible.

I want to keep all user accounts as is. I assume I'll need /etc/passwd and /etc/shadow. Anything else?

I want to keep the web server configs, files. I know to back up /etc/apache2/ and /etc/mysql/ and my web directories(/var/www).

My user directories: /home/

I want to keep my static IP settings. I know to get /etc/network/interfaces. Anything else?

The server doesn't run a DNS server but should I back up any files to keep it's subdomain name?

That's all I can think of at the moment. Can anyone else come up with other important files?

Also, will there be any conflicts with simply replacing these files on the new server?

Thank you for working through this with me! :)

I would make a copy of everything in /etc, and of course /home. Some things will be changed in the config files, but I guess you can fix that by running dpkg-reconfigure for an individual package (since it will see that the configfile has changed)..?

Also, you could restore /etc before you install any packages

On your current install.
```

dpkg --get-selections > installed_pkg

```

On your new install
```

# restore /etc
sudo dpkg --set-selections < installed_pkg
sudo apt-get dselect-upgrade

```

This should prompt you that it has newer versions and should have a merge option somewhere when it notices differences.

I've never done get/set selections when upgrading to a newer version, so some packages may not be installed.

Alternatively you could use my EOL guide to upgrade to a newer Ubuntu version. See my signature for the link :)

---

### Post by Lye on 2009-07-31
Hey thanks for all the help guys! I'm going to upgrade the system tomorrow and just go with my instincts and training. I'm probably over-analyzing the upgrade...it's not a complicated system, just a web server :-)

---

