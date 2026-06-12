---
title: "Speed up firefox... alot! (No-console 1.5 install)"
date: 2005-12-04
forum: General Help
---

### Post by Curlydave on 2005-12-04
(I originally posted this as a "HOW-TO", but it was apparently not approved by moderators.)

This tutorial explains how to quickly install the latest version of Firefox without having to use the console at all. This will greatly improve performance over the gnome-integrated version of firefox. The bolded sections are the primary steps.

1. **Download the latest version of FF from the mozilla website** [http://www.mozilla.com/products/download.html?product=firefox-1.5&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-1.5&os=linux&lang=en-US)

Save this file to your main filesystem directory, "/", or download it to a different directory and move it to your "/" directory.

2. Open a root browser (this can be done by creating a launcher with the following command: "gksudo "nautilus --nodesktop /""), right click on the firefox-1.5.tar.gz file which you have just downloaded, and select "extract here" from the drop-down menu. This will **extract firefox to the directory "/firefox"**

3. **Create a launcher on your desktop** with the following in the command field: "/firefox/firefox". After creating the launcher, right-click on it and select properties. Click the icon change button, and browse to the directory /firefox/icons, and select the icon with a .PNG extension. Select ok again, and exit the properties. You may want to resize the icon by right clicking on your launcher and selecting "stretch icon". You may move a copy of your launcher on a panel if you wish

This should, among other things, greatly improve your FF performance.

---

### Post by GreyFox503 on 2005-12-04
It's not a good idea to just drop new programs onto the root directory / of your system.  I would highly recommend unpacking this somewhere else, like /opt/firefox/ or ~/firefox/

You're right about the speed increase, though.  I'm definitely using FF 1.5 straight from mozilla.

---

