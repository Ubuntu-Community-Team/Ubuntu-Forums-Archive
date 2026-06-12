---
title: "How can I simplify installing Kiba Dock?"
date: 2008-07-14
forum: General Help
---

### Post by MR.UNOWEN on 2008-07-14
Hello,

So I've been using kiba-dock and every time I get a friend to try out Linux I always put Kiba-Dock on. The annoying part is that I have to input a long line of commands in to get it installed. Also the most recent version of it doesn't look so good. Is there a way I can simplify the process into clicking on one file to install the whole thing and use the version I'm currently using????

Here's the commands....

sudo aptitude remove automake1.4

sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev

mkdir kiba-dock
cd kiba-dock

svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/) akamaru

svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/) kiba-dock

svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/) kiba-plugins

svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/) kiba-dbus-plugins

not needed:
svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-gaim-plugin](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-gaim-plugin) kiba-gaim-plugin
svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-ephy-extension](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-ephy-extension) kiba-ephy-extension

cd akamaru/
./autogen.sh --prefix=/usr --exec-prefix=/usr
sudo make install
cd ..

cd kiba-dock/
./autogen.sh
sudo make install 
cd ..

cd kiba-plugins/
./autogen.sh
sudo make install 
cd ..

cd kiba-dbus-plugins/
./autogen.sh
sudo make install
cd ..

---

