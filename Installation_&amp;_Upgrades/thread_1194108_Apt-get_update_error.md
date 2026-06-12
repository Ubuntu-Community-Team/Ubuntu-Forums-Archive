---
title: "Apt-get update error"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by xtjacob on 2009-06-22
I recently had a problem with my sources.list file not being read. I fixed it, but now I get an error when I run sudo apt-get update.
Output in command line is:
```
apt-get: update
Reading package lists... Done
Reading package lists... Done
cp: cannot stat `/var/lib/apt/native/lists/*_*': No such file or directory
```

I've searched everywhere and I looked on other Ubuntu boxes in my house and they don't have have that folder. I have Ubuntu 9.04 x86_64 on an Acer Aspire 4530. Anyone know what could be wrong?:confused:

---

### Post by unutbu on 2009-06-22
Please post the output of these commands
```
sudo find /etc/apt/ -type f -exec grep -l native {} \;
apt-config dump

```

The "sudo find" command searches the /etc/apt/ directory for any file that mentions the word "native".

The "apt-config dump" command prints the configuration options that apt-get is currently using.

---

### Post by xtjacob on 2009-06-22
When I ran the first command I had no output.
Output of apt-config dump is:
```
APT "";
APT::Architecture "amd64";
APT::Build-Essential "";
APT::Build-Essential:: "build-essential";
APT::Install-Recommends "1";
APT::Install-Suggests "0";
APT::Acquire "";
APT::Acquire::Translation "environment";
APT::Authentication "";
APT::Authentication::TrustCDROM "true";
APT::NeverAutoRemove "";
APT::NeverAutoRemove:: "^linux-firmware$";
APT::NeverAutoRemove:: "^linux-image.*";
APT::NeverAutoRemove:: "^linux-restricted-modules.*";
APT::NeverAutoRemove:: "^linux-ubuntu-modules-.*";
APT::Never-MarkAuto-Sections "";
APT::Never-MarkAuto-Sections:: "metapackages";
APT::Never-MarkAuto-Sections:: "restricted/metapackages";
APT::Never-MarkAuto-Sections:: "universe/metapackages";
APT::Never-MarkAuto-Sections:: "multiverse/metapackages";
APT::Periodic "";
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "1";
APT::Update "";
APT::Update::Post-Invoke-Success "";
APT::Update::Post-Invoke-Success:: "touch /var/lib/apt/periodic/update-success-stamp 2>/dev/null || true";
APT::Update::Post-Invoke-Success:: "(sleep 60; /usr/bin/dbus-send --system --dest=org.freedesktop.PackageKit --type=method_call /org/freedesktop/PackageKit org.freedesktop.PackageKit.StateHasChanged string:'cache-update')&";
APT::Archives "";
APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";
Dir "/";
Dir::State "var/lib/apt/";
Dir::State::lists "lists/";
Dir::State::cdroms "cdroms.list";
Dir::State::mirrors "mirrors/";
Dir::State::userstatus "status.user";
Dir::State::status "/var/lib/dpkg/status";
Dir::Cache "var/cache/apt/";
Dir::Cache::archives "archives/";
Dir::Cache::srcpkgcache "srcpkgcache.bin";
Dir::Cache::pkgcache "pkgcache.bin";
Dir::Etc "etc/apt/";
Dir::Etc::sourcelist "sources.list";
Dir::Etc::sourceparts "sources.list.d";
Dir::Etc::vendorlist "vendors.list";
Dir::Etc::vendorparts "vendors.list.d";
Dir::Etc::main "apt.conf";
Dir::Etc::parts "apt.conf.d";
Dir::Etc::preferences "preferences";
Dir::Bin "";
Dir::Bin::methods "/usr/lib/apt/methods";
Dir::Bin::dpkg "/usr/bin/dpkg";
Dir::Log "var/log/apt";
Dir::Log::Terminal "term.log";
aptitude "";
aptitude::Keep-Unused-Pattern "^linux-image.*$ | ^linux-restricted-modules.*$ | ^linux-ubuntu-modules.*$";
aptitude::Get-Root-Command "sudo:/usr/bin/sudo";
Unattended-Upgrade "";
Unattended-Upgrade::Allowed-Origins "";
Unattended-Upgrade::Allowed-Origins:: "Ubuntu jaunty-security";
DPkg "";
DPkg::Pre-Install-Pkgs "";
DPkg::Pre-Install-Pkgs:: "/usr/sbin/dpkg-preconfigure --apt || true";
DPkg::Post-Invoke "";
DPkg::Post-Invoke:: "if [ -d /var/lib/update-notifier ]; then touch /var/lib/update-notifier/dpkg-run-stamp; fi; if [ -e /var/run/updates-available ]; then echo > /var/run/updates-available; fi ";
```

---

### Post by unutbu on 2009-06-22
Hm, the above commands probably are looking in the wrong direction.
According to [http://www.mail-archive.com/debian-devel@lists.debian.org/msg270865.html](http://www.mail-archive.com/debian-devel@lists.debian.org/msg270865.html), there is an alternate version of apt-get which intercepts the "apt-get update" command and runs apt-get.real which reads /var/lib/apt/native.

It sounds like this has to do with using 32-bit libs on a  64-bit processor.

What is the output of 
```

dpkg --get-selections | grep ia32
```

---

### Post by xtjacob on 2009-06-22
It's
```
jacob@Not-Vista:~$ dpkg --get-selections | grep ia32
ia32-apt-get					install
ia32-archive					install
ia32-libs					install
ia32-libs-tools					install
ia32-sun-java6-bin				install
```

---

### Post by unutbu on 2009-06-22
I'm sorry. I don't know enough about ia32-apt-get to advise you about what to do.
Do you know if you need the ia32-apt-get package? Do you know what packages you have installed depend on ia32-apt-get? (If not, you can find out by running
```

sudo apt-get -s remove ia32-apt-get
```

The "-s" flag tells apt-get to simulate the removal of ia32-apt-get, but it doesn't actually change your system.)

If you can afford to remove ia32-apt-get, then I think your problem will be solved because you will revert to the regular apt-get. 

But if you need ia32-apt-get, then I'm unsure what to do.

---

### Post by xtjacob on 2009-06-22
Well I don't know what I have that relies on it I'll give it a try though.

---

### Post by xtjacob on 2009-06-22
I just did the simulated uninstall it only uninstalled one packedge so I assume that means it's not a dependency so should I uninstall it?

---

### Post by unutbu on 2009-06-22
I think it would be safe to try. You can always re-install it if necessary.

Err... hold on...

You might want to run```

ls -l /usr/bin/apt*
```
first. See if you have a file called something like
```

/usr/bin/apt-get.real
```

This I believe is the normal apt-get program. It should get renamed to
/usr/bin/apt-get when ia32-apt-get is removed.

---

### Post by xtjacob on 2009-06-22
Awesome! I removed it and it worked, Thanks. :D

---

### Post by xtjacob on 2009-06-22
> **unutbu said:**
> I think it would be say to try. You can always re-install it if necessary.

Err... hold on...
Why?

---

### Post by unutbu on 2009-06-22
Oh good! Phew! :)

---

### Post by xtjacob on 2009-06-22
Could it have caused a problem?

---

### Post by xtjacob on 2009-06-22
Well just to be on the safe side I reinstalled it, and its still working so I guess it was broken. But now after it updates I get:
```
/usr/bin/apt-get: 101: cannot open /var/lib/apt/foreign/lists/archive.canonical.com_ubuntu_dists_jaunty-backports_main_binary-i386_Packages: No such file
/usr/bin/apt-get: 101: cannot open /var/lib/apt/foreign/lists/archive.canonical.com_ubuntu_dists_jaunty-backports_main_binary-i386_Packages: No such file
mangle: ia32-libs-tools/mangle.cc:402: void mangle(Archlist&, Renamelist&): Assertion `buf_used > 1' failed.
Aborted

```

---

### Post by xtjacob on 2009-06-22
Oh great that dug a bigger hole... When I try to use a package manager I get ```
E: Malformed line 116 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
```

---

### Post by xtjacob on 2009-06-22
**Update**
It messed with my lists file so i fixed it.

---

### Post by unutbu on 2009-06-22
Is it fixed now?

---

### Post by xtjacob on 2009-06-22
Yah, sorry for all the random stuff.

---

### Post by unutbu on 2009-06-22
No problem. Glad you got it sorted out.

---

