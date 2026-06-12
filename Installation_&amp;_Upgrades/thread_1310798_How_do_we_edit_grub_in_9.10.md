---
title: "How do we edit grub in 9.10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by dougalkerr on 2009-11-02
I presume someone knows where the grub or menu.lst file is to edit. I tried to gedit grub.cfg using sudo and was told I don't have permission. What's going on?
I also installed EnvyNG to effect installing the proper ATI driver and I get the window showing with the option to choose the ATI driver (which looks like a very recent one) but, when I try to enable it the next messagebox that shows progress just sits there at 0%. I tried to install the driver through System/Admin.../Hardware Drivers but, again I got no progress. Does anyone know if there is a problem with repositories. I managed a system update without problem.

We are all expecting so much from this release in competition with Windeez 7 but, it is not happening straight off. Such a disappointment.

Cheers...

---

### Post by jwang on 2009-11-02
/boot/grub/menu.lst

You need to have root privilege(or can sudo) to edit.

---

### Post by detroit/zero on 2009-11-02
> **jwang said:**
> /boot/grub/menu.lst

You need to have root privilege(or can sudo) to edit.
You sure about that? You should make sure you have at least some sort of clue before answering a post.

In 9.10, OP, you were right. I just tried it, and the command to edit grub.cfg is```
gksudo gedit /boot/grub/grub.cfg
```Or you can use the text editor of your choice.

---

### Post by davidsrsb on 2009-11-02
menu.1st is a grub file, dougalkerr has grub2 which does not have this
Don't try to edit grub.cfg as it is constantly regenerated
You need to have a look in /etc/grub.d

---

### Post by coffeecat on 2009-11-02
> **detroit/zero said:**
> ```
gksudo gedit /boot/grub/grub.cfg
```

Do **not** edit grub.cfg. Have a look at this Ubuntu documentation"

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

> 

[LIST]
[*]The main menu file, */boot/grub/grub.cfg*, is not meant to be edited, even by 'root'.
[*]*grub.cfg* is overwritten anytime there is a update, a kernel is added/removed, or the user runs update-grub
[/LIST]
@dougalkerr, there is no menu.lst in grub2 which is the version of grub that comes with 9.04. Apart from the above link, you might find this thread useful:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by dougalkerr on 2009-11-07
Well folks I think the new method for editing the boot menu stinks. I have had a look at editing it and can't follow it straight off. So for me this is a big thumbs down. We need things to be simple and straightforward to be able to ward off 'other' operating systems else upgrades are a waste of time - in my humble opinion...

---

### Post by jheaton5 on 2009-11-07
> **dougalkerr said:**
> Well folks I think the new method for editing the boot menu stinks. I have had a look at editing it and can't follow it straight off. So for me this is a big thumbs down. We need things to be simple and straightforward to be able to ward off 'other' operating systems else upgrades are a waste of time - in my humble opinion...

I don't think grub2 is any more complicated than grub-legacy.  It's just that we have been used to working with menu.lst for so long we have gotten complacent.  When I first started trying to customize menu.lst, it was complicated too.  But I learned.  And I am learning grub2 as well.  I disagree that _We_ need things to be simple.  I didn't come to GNU/Linux for simplicity.  I suspect, neither did you.

---

### Post by detroit/zero on 2009-11-07
> **dougalkerr said:**
> We need things to be simple and straightforward to be able to ward off 'other' operating systems else upgrades are a waste of time - in my humble opinion...
What other operating systems do we need to ward off? Why do we need to ward off these other operating systems?

---

### Post by fenario on 2009-11-07
I found my menu looking very messy after installing 9.10
Got refused editing grub.cfg, even with sudo.
used a Puppy-Linux CD to get in the back-door.
Puppies are notorious for disrespecting permissions,
so no worries to #-up a few entries in grub.cfg
now it's just:

Ubuntu 9.10
Windows 7

neat and simple (KISS):p

---

### Post by jheaton5 on 2009-11-07
> **fenario said:**
> I found my menu looking very messy after installing 9.10
Got refused editing grub.cfg, even with sudo.
used a Puppy-Linux CD to get in the back-door.
Puppies are notorious for disrespecting permissions,
so no worries to #-up a few entries in grub.cfg
now it's just:

Ubuntu 9.10
Windows 7

neat and simple (KISS):p

The next time you update your kernel the system will run update-grub and all your changes will be wiped out.  You need to learn the proper way to modify grub2.  Puppies sometimes mess all over the floor.

---

### Post by coffeecat on 2009-11-08
> **fenario said:**
> I found my menu looking very messy after installing 9.10
Got refused editing grub.cfg, even with sudo.
used a Puppy-Linux CD to get in the back-door.
Puppies are notorious for disrespecting permissions,
so no worries to #-up a few entries in grub.cfg
now it's just:

Ubuntu 9.10
Windows 7

neat and simple (KISS):p

> **coffeecat said:**
> Do **not** edit grub.cfg. Have a look at this Ubuntu documentation"

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

:sigh:  ](*,)

---

### Post by Danielaus on 2009-11-08
Hi guys, I was playing with Grub2 conf files and had a few issues:
1) At boot grub loads the menu but there is no timeout, it just sits there waiting for me to press enter
2) I was not able to put a special menuentry as separator between ubuntu entries and windows entry: it shows in grub.cfg but doesn't in the boot menu...

can someone please help me figure out what the problem is? thank you!!
here are my configuration files:

/boot/grub/grub.cfg
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 8d50f079-48e6-468c-b77e-7f4f6a37438c
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 8d50f079-48e6-468c-b77e-7f4f6a37438c
insmod tga
if background_image /usr/share/images/grub/Plasma-lamp.800.tga ; then
  set color_normal=white/black
  set color_highlight=black/white
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu karmic 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 8d50f079-48e6-468c-b77e-7f4f6a37438c
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8d50f079-48e6-468c-b77e-7f4f6a37438c ro    splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu karmic 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 8d50f079-48e6-468c-b77e-7f4f6a37438c
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8d50f079-48e6-468c-b77e-7f4f6a37438c ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/29_other ###
menuentry "------Other Operating Systems------" {
    set root=(hd0,2)
}
### END /etc/grub.d/29_other ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows Seven Ultimate (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 5a3474db3474bb97
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```/etc/default/grub
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT="3"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=" splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=800x600

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to disable generation of menu entries for other os
#GRUB_DISABLE_OS_PROBER=true
```/etc/grub.d/00_header
```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

transform="s,x,x,"

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
grub_prefix=`echo /boot/grub | sed ${transform}`

. ${libdir}/grub/grub-mkconfig_lib

# Do this as early as possible, since other commands might depend on it.
# (e.g. the `loadfont' command might need lvm or raid modules)
for i in ${GRUB_PRELOAD_MODULES} ; do
  echo "insmod $i"
done

if [ "x${GRUB_DEFAULT}" = "x" ] ; then GRUB_DEFAULT=0 ; fi
if [ "x${GRUB_DEFAULT}" = "xsaved" ] ; then GRUB_DEFAULT='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT}" = "x" ] ; then GRUB_TIMEOUT=3 ; fi
if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=800x600 ; fi

cat << EOF
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="${GRUB_DEFAULT}"
if [ \${prev_saved_entry} ]; then
  saved_entry=\${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
EOF

case ${GRUB_TERMINAL_INPUT}:${GRUB_TERMINAL_OUTPUT} in
  serial:* | *:serial)
    if ! test -e ${grub_prefix}/serial.mod ; then
      echo "Serial terminal not available on this platform." >&2 ; exit 1
    fi

    if [ "x${GRUB_SERIAL_COMMAND}" = "x" ] ; then
      grub_warn "Requested serial terminal but GRUB_SERIAL_COMMAND is unspecified. Default parameters will be used."
      GRUB_SERIAL_COMMAND=serial
    fi
    echo "${GRUB_SERIAL_COMMAND}"
  ;;
esac

case x${GRUB_TERMINAL_INPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
if terminal_input ${GRUB_TERMINAL_INPUT} ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_input
  terminal ${GRUB_TERMINAL_INPUT}
fi
EOF
  ;;
esac

case x${GRUB_TERMINAL_OUTPUT} in
 xgfxterm)
    # Make the font accessible
    prepare_grub_to_access_device `${grub_probe} --target=device ${GRUB_FONT_PATH}`

    cat << EOF
if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
set gfxmode=800x600
  insmod gfxterm
  insmod ${GRUB_VIDEO_BACKEND}
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
EOF
  ;;
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
if terminal_output ${GRUB_TERMINAL_OUTPUT} ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_output
  terminal ${GRUB_TERMINAL_OUTPUT}
fi
EOF
  ;;
esac

cat << EOF
if [ \${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=${GRUB_TIMEOUT}
fi
EOF
```/etc/grub.d/10_linux
```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR}"
fi

# loop-AES arranges things so that /dev/loop/X can be our root device, but
# the initrds that Linux uses don't like that.
case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
    # We can't cope with devices loop-mounted from files here.
    case ${GRUB_DEVICE} in
      /dev/*) ;;
      *) exit 0 ;;
    esac
  ;;
esac

if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
    || [ "`grub-probe -t abstraction --device ${GRUB_DEVICE} | sed -e 's,.*\(lvm\).*,\1,'`" = "lvm"  ] ; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi

# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi

linux_entry ()
{
  cat << EOF
menuentry "$1" {
        recordfail=1
        if [ -n \${have_grubenv} ]; then save_env recordfail; fi
EOF
  if [ "x$3" = "xquiet" ]; then
    cat << EOF
    set quiet=1
EOF
  fi
  save_default_entry | sed -e "s/^/\t/"
  prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/"
  cat << EOF
    linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2
EOF
  if test -n "${initrd}" ; then
    cat << EOF
    initrd    ${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"
  # user-added variable
  codename="`lsb_release -cs`"

  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
       "initrd-${version}" "initrd.img-${alt_version}" \
       "initrd-${alt_version}.img" "initrd-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  linux_entry "${OS} ${codename} ${version}" \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}"
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS} ${codename} ${version} (recovery mode)" \
    "single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
done
```/etc/grub.d/29_other
```
#!/bin/sh
exec tail -n +3 $0
menuentry "------Other Operating Systems------" {
    set root=(hd0,2)
}

```

---

### Post by Danielaus on 2009-11-08
> **Danielaus said:**
> 
1) At boot grub loads the menu but there is no timeout, it just sits there waiting for me to press enter

solved this modifying /etc/grub.d/00_header from
```
.....
cat << EOF
if [ \${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=${GRUB_TIMEOUT}
fi
EOF
```to
```
cat << EOF
## Force Timeout
# if [ \${recordfail} = 1 ]; then
#   set timeout=-1
# else
  set timeout=${GRUB_TIMEOUT}
# fi
EOF
```does anyone know what \${recordfail} means?

---

### Post by Danielaus on 2009-11-16
bump :arrow:

---

### Post by JHCKX on 2009-11-16
What's so hard? Ubuntu 9.10 uses grub2, a quick google of "ubuntu grub2 configure" points to [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Detailed instructions there, including the following: "Some of the most common changes, such as the default OS/kernel and menu timeout, can be changed from within a GUI app called StartUp-Manager." I installed startup-manager, it works fine with grub2 as well as the older grub.

Or am I missing something?

---

### Post by coffeecat on 2009-11-16
> **John2.Hendrickx@gmail.com said:**
> What's so hard? Ubuntu 9.10 uses grub2, a quick google of "ubuntu grub2 configure" points to [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Detailed instructions there, including the following: "Some of the most common changes, such as the default OS/kernel and menu timeout, can be changed from within a GUI app called StartUp-Manager." I installed startup-manager, it works fine with grub2 as well as the older grub.

Or am I missing something?

Well - you missed the fact that I posted that same link in this thread two weeks ago. :rolleyes:

:wink:

---

