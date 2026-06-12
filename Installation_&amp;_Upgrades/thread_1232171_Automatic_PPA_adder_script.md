---
title: "Automatic PPA adder script"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by Vermind on 2009-08-05
Sometimes we all wish to have the latest piece of software installed. When we do not want to deal with compiling things from source, we use PPAs or Personal Package Archives set up by other Ubuntu users. For example, [here is the PPA of Spring]("https://launchpad.net/~spring/+archive/ppa"), the open-source strategy game and multiplayer client, and [here is the PPA of the Pidgin IM client]("https://launchpad.net/~pidgin-developers/+archive/ppa"). The PPA pages usually have some instructions on how to install them. The instructions include adding lines to configuration files such as system software sources and adding the PPA's public key into your recognized authentication keys. While this takes only a few minutes, it is tiresome to do this every time when adding a PPA, especially if you try out a lot of PPAs. [B]This is why I have created a script that automatically adds the PPA into your software sources, and the public key into the authentication keys.
The script is attached to this post.[/B]
**Update: the script now detects your distribution and adds PPAs for it, instead of adding ppas just for jaunty.**
Instructions:
[LIST=1]
[*]Save the script to any folder.
[*]right-click the script and choose properties.
[*]On the Permissions tab, check "Allow executing the file as a program"
[*]Double-click the script to run it. Choose 'Run'. Follow instructions.
[*]The script will ask the address of the PPA. You can copy and paste the address from your web browser's address bar. Example address: [https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)
[/LIST]

After the script is done, you can open Synaptic and press the reload button. The contents of the PPA are now available in Synaptic.

To remove a PPA, you can use the Ubuntu software sources dialog. This is available from System - Administration - Software sources or from the Synaptic menu, in Settings - Repositories. Added PPAs are on the "Third party sources" tab.

For completeness, I include here a step-by-step explanation of what the script does. Here is the procedure:
[LIST=1]
[*] Check if zenity, the GTK+ dialog application is installed. Ask the user's password and install it with apt if not.
[*] Use zenity to ask the PPA address.
[*] download the PPA HTML page from the address.
[*] read the page for the public key identifier. Receive and add it with apt-key from keyserver.ubuntu.com
[*] Find the deb lines from the page. Add the Jaunty lines into /etc/apt/sources.list.d/ppaname.list, where ppaname is the name part of the PPA address, for example spring or pidgin-developers.
[*] Lines are added with tee, and existing PPAs will be replaced if they have the same name. Same names are unlikely, since a PPA in Launchpad needs to have a unique name.
[/LIST]

Note: the script adds Jaunty lines by default. You can modify it to add other Ubuntu release lines. You can also change the added lines from the software sources, or Synaptic's Repositories. Just change the instances of jaunty to your release.

Another note: Right now the script only supports Launchpad PPAs. If the PPA's sources.list entries mentioned on the page do not start with [http://ppa.launchpad.net](http://ppa.launchpad.net), I do not guarantee the script will work.

---

### Post by laceration on 2009-08-21
Nice, this will come in useful.  Thank you.  Since I am still using Hardy, I replaced
```

dist="karmic"

```
with
```

hardy=$(locate /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_source_Sources | wc -l)
intrepid=$(locate /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid_main_source_Sources | wc -l)
jaunty=$(locate /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_main_source_Sources | wc -l)
karmic=$(locate /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_main_source_Sources | wc -l)
if [ $hardy -gt 0 ]
then
dist="hardy"
fi
if [ $intrepid -gt 0 ]
then
dist="intrepid"
fi
if [ $jaunty -gt 0 ]
then
dist="jaunty"
fi
if [ $karmic -gt 0 ]
then
dist="karmic"
fi

```
This will make the script operational through my upgrade path or for the user of any distribution since hardy without having to alter it.

---

### Post by Vermind on 2009-08-26
Hi laceration,
thanks for your input!
How about looking at the /etc/lsb-release file?
We can do this:
```
source /etc/lsb-release
echo $DISTRIB_CODENAME
```

I will update the post with a version that gets the dist value like this shortly.

---

### Post by laceration on 2009-08-26
That's a much better way to do it and it would work for forever.
```

source /etc/lsb-release
dist=$DISTRIB_CODENAME

```
You should make a PPA for it just for the irony!

---

### Post by Vermind on 2009-12-19
Nowadays, in Karmic,
adding a ppa can be accomplished with one command:
```
sudo add-apt-repository ppa:ppaname
```
Where ppaname is the name of the ppa. This also adds the corresponding gpg keys, so my script is becoming obsolete. Of course, my script is still a nice GUI thingy that you can put into nautilus-scripts, while this new command is a console thing :). The names can be read from launchpad ppa pages.
Examples:

```
sudo add-apt-repository ppa:spring/ppa
```
```
sudo add-apt-repository ppa:pidgin-developers/ppa
```

---

