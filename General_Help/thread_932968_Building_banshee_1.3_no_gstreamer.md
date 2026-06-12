---
title: "Building banshee 1.3: no gstreamer?"
date: 2008-09-29
forum: General Help
---

### Post by wolterh on 2008-09-29
Hi. I've downloaded the latest unstable version of banshee, but i cannot build it.
When I run ./configure it all goes fine until it says that...
```
checking for GST... configure: error: Package requirements (gstreamer-0.10 >= 0.10.3
		gstreamer-base-0.10 >= 0.10.3
		gstreamer-plugins-base-0.10 >= 0.10.3
		gstreamer-controller-0.10 >= 0.10.3
		gstreamer-dataprotocol-0.10 >= 0.10.3) were not met:

No package 'gstreamer-0.10' found
No package 'gstreamer-base-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'gstreamer-controller-0.10' found
No package 'gstreamer-dataprotocol-0.10' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GST_CFLAGS
and GST_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

So, I do not know what to do next. I know that I have gstreamer 0.10, but it is recorded as gstreamer0.10-xxx, so i guess that that missmatch is making the error.

Even though the console outputs some GST_FLAGS suggestions, i do not have the most remote idea of how to do it.

---

### Post by crossz on 2008-10-27
check this out. same question with yours.
[http://forums.fedoraforum.org/showthread.php?t=202552](http://forums.fedoraforum.org/showthread.php?t=202552)

```
%define mono_shared %{_builddir}/%{?buildsubdir}

Name:    banshee
Version: 1.3.3
Release: 1%{?dist}
Summary: Easily import, manage, and play selections from your music collection
Group:   Applications/Multimedia
License: MIT
URL:     http://banshee-project.org/
Source0: http://banshee-project.org/files/banshee/banshee-1-%{version}.tar.bz2
Source1: README.Fedora
BuildRoot: %{_tmppath}/%{name}-%{version}-%{release}-root-%(%{__id_u} -n)

# We only have mono on these arches:
ExclusiveArch: %ix86 x86_64 ia64 armv4l sparc alpha ppc

# Versioned dependencies
BuildRequires: libmusicbrainz-devel >= 2.1.1
BuildRequires: mono-devel >= 1.1.10
BuildRequires: mono-zeroconf-devel >= 0.7.2
BuildRequires: hal-devel >= 0.5.6
BuildRequires: sqlite-devel >= 3.3
BuildRequires: gstreamer-devel >= 0.10
BuildRequires: gstreamer-plugins-base-devel >= 0.10
BuildRequires: gstreamer-plugins-good >= 0.10
BuildRequires: libmtp-devel >= 0.2.0
BuildRequires: ipod-sharp-devel >= 0.8.1

# Sharp
BuildRequires: avahi-sharp gtk-sharp2-devel taglib-sharp-devel gnome-sharp-devel

# Extra mono deps
BuildRequires: mono-data mono-data-sqlite mono-addins-devel

# Gnome/Glib
BuildRequires: gnome-desktop-devel nautilus-cd-burner-devel ndesk-dbus-glib-devel

# Misc
BuildRequires: gettext-devel perl(XML::Parser)

# No boo-devel for ppc but we owe it to the users to keep banshee up to date
%ifarch  %ix86 x86_64 sparc
BuildRequires: boo-devel
%endif
```

Also, ipod-sharp-devel-0.8.1 is needed.

---

### Post by directhex on 2008-10-27
apt-get build-dep banshee.

If you don't know about build-dep, are you sure you want to compile things yourself? Especially considering the packages on [https://launchpad.net/~banshee-unstable-team/+archive](https://launchpad.net/~banshee-unstable-team/+archive)

---

### Post by wolterh on 2008-10-27
Thanks both. This was solved long with a solution similar to the one provided on the previous reply. My bad for forgeting that this post was still alive.

---

