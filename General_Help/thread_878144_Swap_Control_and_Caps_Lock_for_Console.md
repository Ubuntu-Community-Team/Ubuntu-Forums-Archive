---
title: "Swap Control and Caps Lock for Console"
date: 2008-08-02
forum: General Help
---

### Post by izzydahedgehog on 2008-08-02
While I've figured out how to swap caps lock and control in X, I can't figure out how to do it in Ubuntu from the command line.  The best tutorial I've found, [http://www.manicai.net/comp/swap-caps-ctrl.html](http://www.manicai.net/comp/swap-caps-ctrl.html), mentions a "keymap.gz" file but Ubuntu doesn't seem to have one.  Does anyone know how to change keymaps in Ubuntu from the console?

---

### Post by pauper on 2008-08-03
If you are refering to text console (Ctrl-Alt-Fn), then try the following
procedure.

Here: default keys are CapsLock (keycode 5[noparse]8[/noparse]), Control_L (keycode 29).
If you need Control_R as CapsLock change keycode value to 97. 

```
**grep XKB /etc/default/console-setup**
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS="compose:menu"
**ls /usr/share/keymaps**
[color=blue]amiga  atari  i386  include  mac  sun[/color]

# First, choose your architecture (uname -m), later layout--QWERTY, DVORAK,
# etc. Make a backup copy of defkeymap.kmap.gz
# By the way, one can choose any other keymap. Just make sure its reflected
# later in your bootmisc.sh script.

[b]sudo cp /usr/share/keymaps/i386/qwerty/defkeymap.kmap{,.OLD}.gz
gunzip -c /usr/share/keymaps/i386/qwerty/defkeymap.kmap.gz > ~/defkeymap.kmap
sed -i -e 's/29 = Control/29 = Caps_Lock/' ~/defkeymap.kmap
sed -i -e 's/58 = Caps_Lock/58 = Control/' ~/defkeymap.kmap
gzip -9 ~/defkeymap.kmap
sudo mv ~/defkeymap.kmap.gz /usr/share/keymaps/i386/qwerty
sudo chown root:root /usr/share/keymaps/i386/qwerty/defkeymap.kmap.gz[/b]

# Load for the current session. Again, if you choose uk.kmap.gz, for example,
# you should run "sudo loadkeys /path/to/uk.kmap.gz" instead.

**sudo loadkeys --default**
```

Make it permanent:

```
sudo vim /etc/rcS.d/S**bootmisc.sh
```

Type in "loadkeys --default" past PATH variable and before "do_start":

[php]PATH=/usr/sbin:/usr/bin:/sbin:/bin
[ "$DELAYLOGIN" ] || DELAYLOGIN=yes
. /lib/init/vars.sh

loadkeys --default

do_start () {
	#
	# If login delaying is enabled then create the flag file
	# which prevents logins before startup is complete
	#[/php]

---

### Post by uniq on 2008-11-07
```

sudo sensible-editor /etc/default/console-setup

```Edit the XKBOPTIONS line
```

XKBOPTIONS="ctrl:swapcaps"

```
save it, and apply from a console ([COLOR="Red"]not from within X![/COLOR]) with

```

sudo /etc/init.d/console-setup start

```

It's probably exactly the same in debian.
See /usr/share/doc/console-setup/README.gz for more.


Have fun :)

---

