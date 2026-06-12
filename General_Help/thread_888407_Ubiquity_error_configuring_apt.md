---
title: "Ubiquity error configuring apt"
date: 2008-08-13
forum: General Help
---

### Post by chris4585 on 2008-08-13
Hello! I'm trying to make a livecd and while ubiquity is running I get this error:

[http://i35.tinypic.com/2v3g3fo.jpg]("http://i35.tinypic.com/2v3g3fo.jpg")

The odd thing is, I don't seem to be missing any packages that I need, nor do I get any errors after the system is installed.  Any help would be greatful

EDIT: would it also make any difference if I added this repo?

[http://crunchbang.org/archives/2008/03/08/crunchbang-linux-apt-repository/]("http://crunchbang.org/archives/2008/03/08/crunchbang-linux-apt-repository/")

---

### Post by chris4585 on 2008-08-14
Nothing? I figured someone would have a idea? :/

---

### Post by chris4585 on 2008-08-21
Ok, I might of solved my error, on my system I'm building if I delete

/usr/lib/ubuiqity/apt-setup/50cdrom

which contains:

```
#!/bin/sh
set -e

. /usr/share/debconf/confmodule

file="$1"

logoutput=""
if [ "$CATCHLOG" ]; then
	logoutput="log-output -t apt-setup"
fi

chroot=
if [ "$ROOT" ]; then
	chroot=chroot
fi

tmp=$($chroot $ROOT tempfile)

# apt-cdrom can be interactive, avoid that
if $logoutput $chroot $ROOT apt-cdrom add \
   -o Dir::Etc::SourceList=$tmp \
   </dev/null; then
	cat $ROOT$tmp >> $file
else
	rm -f $ROOT$tmp $ROOT$tmp~
	db_input critical apt-setup/cdrom/failed || true
	db_go || exit 10
fi

rm -f $ROOT$tmp $ROOT$tmp~

```

I don't get that error anymore, but is there a more proper way of doing this? or would I delete something I don't want to delete by doing that?

---

### Post by chris4585 on 2008-08-21
would anyone know where I could edit ubiquity to change the exec of the dialog that asks you to either restart your computer or continue using the livecd?

In my livecd when ubiuqity is done and I hit restart the whole thing freezes

---

