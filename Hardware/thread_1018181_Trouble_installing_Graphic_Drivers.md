---
title: "Trouble installing Graphic Drivers"
date: 2008-12-21
forum: Hardware
---

### Post by MTGap on 2008-12-21
Well I have these drivers... and I'm attempting to install them, but I'm having troubles. Currently it is the MESA drivers (the ones with the gears) and I'm having trouble with the graphics when opening up apps because there will be a flash of black. Also for totem player the screen will go black when I click on it. So I'm trying to fix my graphic issues with these drivers.

Here are the installation notes, I was able to create the X11R6 folder in usr, but wasn't able to put anything in it. Where should I put my tar.gz so that I can extract it into there?

```

Summary: DRI Package
Name: i915Graphics 
Version: %{dri_ver}
Release: %{dri_rel}
Group: Drivers
Copyright: MIT/X
Source: %{name}.tar.gz
BuildArch: i386

%description
i915G DRI driver package

%prep
cp $RPM_SOURCE_DIR/i915Graphics.tar.gz .

%build

%install
rm -fr $RPM_BUILD_ROOT
mkdir -p $RPM_BUILD_ROOT/usr/X11R6/dripkg
cp $RPM_SOURCE_DIR/i915Graphics.tar.gz $RPM_BUILD_ROOT/usr/X11R6/dripkg

%clean
rm -fr $RPM_BUILD_ROOT

%post
cd /usr/X11R6/dripkg
tar zxf i915Graphics.tar.gz
cd dripkg
if [ ! -d /var/lib/dripkg ]; then
	mkdir /var/lib/dripkg
fi
cp install.sh pkginfo /var/lib/dripkg
if ! ./install.sh -b; then
	echo ""
	echo "Package is installed, but not configured."
	echo "You'll need to use rpm -e to remove this package before re-installing."
fi
cd ..
rm -fr dripkg

%preun
cd /var/lib/dripkg && ./install.sh -b restore

%files
%defattr(-,root,root)
/usr/X11R6/dripkg/i915Graphics.tar.gz

```

---

