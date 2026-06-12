---
title: "audiosink value has the tag &quot;This key is not writeable sound problem"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by kamwla on 2007-06-12
This happened after the installing  intel hda drivers.
when i try to open system>preferences>sound I get his message
'
'The application "gnome-sound-properties" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application.''

when i go to details i get

Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/gstreamer/0.10/default/audiosink' set in a read-only source at the front of your configuration path
Any ideas how to deal with it 

 Every attempt to edit audiosink by using sudo gconf-editor comes up with a read only error despite the fact that i am logged in as a root user.
I use Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller on Toshiba P100-188

Many thanks for any and all suggestions.

---

