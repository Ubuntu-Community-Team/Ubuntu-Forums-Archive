---
title: "Backup / Restore problem with Evolution"
date: 2008-11-11
forum: General Help
---

### Post by Happibun on 2008-11-11
Hi,

I am having a problem installing my Evolution folders from my backup.


I know that this is what I need to do - 

** How can I transfer all my Evolution data between computers/to a new partition/to a new computer? **

 Make sure you haven't started Evolution on the new computer/new partition yet. First of all, shut Evolution and its background processes (Evolution Data Server, Evolution Alarm Notify) completely down by using evolution --force-shutdown. Then copy the contents of $HOME/.evolution/, $HOME/.gnome2_private/Evolution (if the old Evolution version is 2.12 or earlier), $HOME/.camel_certs. Then dump your Evolution settings stored in GConf by running gconftool-2 --dump /apps/evolution > some-file.xml where some-file.xml is the name of the file the information is written to. On the new computer, make sure you are not running gconf (by ps ax | grep gconf for example; you normally have to leave gnome for that and then run gconftool-2 --shutdown). Then import those settings by running gconftool-2 --load some-file.xml and log in to gnome again. If you cannot dump your Evolution settings in GConf anymore (e.g. no boot access to the old system), copying the data (cp -R oldComputer/~/.gconf/apps/evolution newComputer/~/.gconf/apps) will do as well (but make sure that this is done while GNOME and the gconf daemon are not running, see above).


but I am sorry, this is all gobbldygook to me. What is more, I have inadvertently already started evolution up to try and sort this out.


Someone please tell me what I need to do in easy step by step instructions that would not completely freak a noob out.


Thanks.

---

