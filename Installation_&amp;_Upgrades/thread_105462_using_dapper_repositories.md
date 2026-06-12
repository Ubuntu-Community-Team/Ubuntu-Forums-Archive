---
title: "using dapper repositories"
date: 2005-12-18
forum: Installation &amp; Upgrades
---

### Post by rplantz on 2005-12-18
I need to upgrade samba from 3.0.14 (breezy version) to 3.0.20, which is in the dapper repositories. What is the "proper" way to get a few packages from the upcoming release?

I did this last week by making two copies -- sources.list_br and sources.list_dap with the appropriate names in them. Then I
1. copied the one I wanted to use to sources.list
2. launched synaptic
3. reloaded
4. installed the package I wanted.

Although it works, this seems awkward to me. I noticed in the unofficial guide [http://www.ubuntuguide.org](http://www.ubuntuguide.org) an item on "How to backup/restore downloaded repositories cache." It says:
```

   2. To backup downloaded repositories cache

sudo tar zcvf apt.tgz /etc/apt/ /var/lib/apt/ /var/cache/apt/

   3. To restore downloaded repositories cache

sudo tar zxvf apt.tgz -C /

```

I could follow this general procedure to create two tarballs, apt_br.tgz and apt_dap.tgz, then use the one I want.

Any thoughts on the best way to do this?

By the way, the reason for upgrading my samba is so that I can browse for my ubuntu file server from my Mac. Tiger does something when browsing that 3.0.14 doesn't like, but 3.0.20 does.

And the reason I'm doing this over again is that I did a complete reinstall. And I mucked up that process, causing me to be very, very thankful for simple backup. Life is a learning process.

---

### Post by matthew on 2005-12-18
Out of the two ideas you mentioned I would use the same method you used--with the two files, copying whichever set of sources I wanted to use to be the current sources.list

You could also put all the repos in your sources.list and comment out those you are not using currently, just adding the Breezy repos when there is a specific program you want and then commenting them out again. This is how I generally do it...be careful, though. Sometimes you run into interesting dependency problems when you mix repositories...this is why the backports project exists. It takes a bit longer for a backport request to go through, but if it can be done jdong will do it.

---

### Post by nanuck on 2005-12-18
I've spent all night and this morning researching this exact mac problem.. decided to sign up to ask the exact same question.. low and behold you beat me :D

i beg you to post your solution and how it worked out..

---

### Post by rplantz on 2005-12-18
[QUOTE=nanuck]I've spent all night and this morning researching this exact mac problem.. decided to sign up to ask the exact same question.. low and behold you beat me :D[/QUOTE]

Here's what I did.
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list_br
sudo cp /etc/apt/sources.list /etc/apt/sources.list_dap
sudo gedit /etc/apt/sources.list_dap

```
Then modify sources.list_dap according to
[http://www.ubuntuforums.org/showthread.php?t=104656&highlight=repositories](http://www.ubuntuforums.org/showthread.php?t=104656&highlight=repositories)
post #2.
Save the changes and quit gedit. Then
```

sudo cp /etc/apt/sources.list_dap /etc/apt/sources.list

```
Start Synaptic and click on Reload.

Scroll down to samba. It should be version 3.0.20b. If you mark it for install, it should require ```

lsb-base
samba-common
smbclient

```
While I was here, I also installed swat, which is supposed to allow you to configure samba from a web browser. (Have to do some other things to get it two work. I'll post that later.)

Quit Synaptic.

This is a good time to restore the breezy sources.list. Otherwise you will continue to get messages saying that upgrades are available, etc. (I installed some other dapper things a few days ago and ended up restoring my whole system! In general, do not mix any package that starts with "lib".)
```

sudo cp /etc/apt/sources.list_br sources.list

```
Start Synaptic again and click on Reload.

When I did this, it did not like my installation CD as a repository. If you wish to keep  it in the list, go to Edit->Add CD-ROM. Then you can click on Reload again.

Now for samba. Here's what I did.
```

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_back
sudo gedit /etc/samba/smb.conf

```
The only changes I made in this file are:
1. I changed the name in workgroup = MSHOME at the beginning of the global section to a name of my own choosing. As far as I know, you can make up any name here, unless you are trying to connect to a network that already has a name.
2. I changed writable = no to writable = yes and set some masks:
```

[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0644

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0755

```
3. I commented out the following section (with the ; at the beginning of each line);
```

;[print$]
;   comment = Printer Drivers
;   path = /var/lib/samba/printers
;   browseable = yes
;   read only = yes
;   guest ok = no

```

Note: If you wish to share your ubuntu printer with the Mac, simply add it as a network printer on the Mac. Ubuntu uses cups, which supports network printers.

Save and quit gedit. Then do
```

sudo smbpasswd -a an_existing_user_name
{provide the user with a password}
sudo /etc/init.d/samba restart

```

Where an_existing_user_name is an account that already exists on the ubuntu machine, and {provide the user with a password} means follow the dialog on the screen.

If you wish to learn more about samba, there's a very good book online at [http://www.faqs.org/docs/samba/toc.html](http://www.faqs.org/docs/samba/toc.html). In particular, chapter six discusses the smb.conf file. I learned a lot from reading that.

Now on the Mac, in the finder do Go->Connect to Server... and click on Browse. In the finder window click on Network.

This should bring up the workgroup name you invented above. Click on that and you should see your ubuntu computer hostname. Click on that and you should get a dialog that asks for an_existing_user_name's password. Use the smb password here. (When I say "click" on the Mac, I'm in list view; other views require that you double-click.)

Please let us know whether or not this works, any errors you find, and any improvements you have.

Oh, and take a nap, since you were working on this all night. :-)

---

### Post by rplantz on 2005-12-18
To get swat to work, I followed the instructions at [http://www.watsky.net/cgi-bin/yabb/YaBB.cgi?board=BOFH;action=display;num=1107570812](http://www.watsky.net/cgi-bin/yabb/YaBB.cgi?board=BOFH;action=display;num=1107570812)

I have only used it so far to look at things.

I've heard that swat can be a security risk. I'm behind a router firewall, but I don't know how well that protects me.

---

### Post by nanuck on 2005-12-19
Well I was getting impatient so I decided to just try an install and change just the apt sources (much like you wrote).. I didn't install a wm, but  everything worked fine from the console (apt-get install samba smbclient), then edited the apt sources back to the original breezy repositories.. all works like a charm.. the mini can now see ubuntu on the network wohoooo :D

I'll keep an eye out if you post about swat.. yet to try it, but sounds like it may be fun to play with!

Thanks for the post, I'm sure i won't be the last to go crazy over this!

---

### Post by ruffneck on 2006-04-11
This is great info. Works a charm rplantz. Thanks plenty!!

---

### Post by Syco54645 on 2006-04-11
i usually just compile newer versions of apps from source.  i did this with kde multiple times.

it is fairly easy to do (have been using linux with no package management for years).

all that you must do is get the source and extract it.  lets say the package is called foo-2.14.tgz (or some type of gzip)

you would simply do
```
tar zxvf foo-2.14.tgz
cd foo-2.14
./configure
make
sudo checkinstall
```

this is of course assuming that they follow the standard make file.
if the package is called foo-2.14.tar.bz2 (or some type of bzip)

you would do
```
tar jxvf foo-2.14.tar.bz2
cd foo-2.14
./configure
make
sudo checkinstall
```

the checkinstall will create a .deb file then install it with apt, thus allowing your database of apps installed to be up to date.

this will work for you as long as none of the dependencies have changed for the app that you wish to install.  if the dependencies have change, then have fun with the dependency game.

hope this helps

-Syco54645

---

### Post by jdong on 2006-04-11
Please, **DO NOT** (that is do NOT) install Dapper packages onto Breezy. You can cause yourself some major headaches now and later when upgrading, if your system survives that far.

If you'd like new packages, build then from source using Debian build tools, or request them through Backports.

[http://ubuntuforums.org/showthread.php?t=12040](http://ubuntuforums.org/showthread.php?t=12040)

This is a rough guide to doing it that I wrote up for Backports a while back.

---

