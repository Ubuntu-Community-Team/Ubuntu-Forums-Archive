---
title: "Installing Compiz plugins Howto"
date: 2008-07-31
forum: General Help
---

### Post by chunchengch on 2008-07-31
Although there are enough effects with the standard installation of the Compiz, sometimes we still want to try some experimental and new plugins, here is my personal summary of installing extra plugins in Compiz, hope this will be helpful for Linux newbie like me.

First, you can download Compiz plugins from these two links:
[http://gitweb.compiz-fusion.org/?o=age](http://gitweb.compiz-fusion.org/?o=age)
[http://wiki.compiz-fusion.org/CompizFusionPlugins](http://wiki.compiz-fusion.org/CompizFusionPlugins)

Assume the plugin you download is [COLOR="SeaGreen"]compizplugin.tar.gz[/COLOR], now we start to install it with following steps:

1. installing necessary dependencies:

[COLOR="Red"]$ sudo apt-get install compiz-bcop compiz-dev libtool build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libgl1-mesa-dev libglu1-mesa-dev autoconf intltool xsltproc[/COLOR]

2. create a folder for the plugin, then move the [COLOR="SeaGreen"]compizplugin.tar.gz[/COLOR] downloaded to this folder and extract it, now we have a new folder [COLOR="Red"]~/Compiz-Plugins/[/COLOR][COLOR="SeaGreen"]compizplugin[/COLOR]:

[COLOR="Red"]$ mkdir ~/Compiz-Plugins
$ cd ~/Compiz-Plugins
$ tar -zvxf [/COLOR][COLOR="SeaGreen"]compizplugin.tar.gz[/COLOR]

3. install plugin:

[COLOR="Red"]$ cd ~/Compiz-Plugins/[/COLOR][COLOR="SeaGreen"]compizplugin[/COLOR]
[COLOR="Red"]$ make clean
$ make
$ sudo make install[/COLOR]

4. logout and re-login

5. now you can open CompizConfig Settings Manager (CCSM) to activate the plugin just installed.

6. remove plugin:

It is very easy to remove the plugin just installed, go to these two folder ~/.compiz/metadata and ~/.compiz/plugins, then remove the relevant files. 

[COLOR="Red"]$ sudo rm -r ~/.compiz/metadata/[/COLOR][COLOR="SeaGreen"]compizplugin[/COLOR][COLOR="Red"].xml[/COLOR]
[COLOR="Red"]$ sudo rm -r ~/.compiz/plugins/lib[/COLOR][COLOR="SeaGreen"]compizplugin[/COLOR][COLOR="Red"].so[/COLOR] 


Here are screenshots and wizard.tar.gz of Wizard plugin I installed, just for your reference.

[ATTACH]79572[/ATTACH]

[ATTACH]79570[/ATTACH]  [ATTACH]79571[/ATTACH]

---

### Post by JOHNNYG713 on 2010-01-14
This is a very good how to ! you can do that, (Great for learning, or 32Bit ) Or ( If your lazy ) for 64Bit deb package of all the new plugins go here !
[http://gnome-look.org/content/show.php/New+compiz+plugin%27s?content=118511](http://gnome-look.org/content/show.php/New+compiz+plugin%27s?content=118511)
This installs all the new plugins for compiz 64Bit !! :D Again these are experimental !
I have used them for some time now with no issues ! To remove plugins, see the above "how to".

---

