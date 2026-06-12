---
title: "apt-get upgrade fails for 8.04.1 Server"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by miceng on 2009-01-09
Hi,

As of this morning I am unable to run apt-get upgrade on Ubuntu server LTS. Here is the output:

# apt-get install util-linux -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  util-linux
1 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
1 not fully installed or removed.
Need to get 0B/440kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 34002 files and directories currently installed.)
Preparing to replace util-linux 2.13.1-5ubuntu2 (using .../util-linux_2.13.1-5ubuntu3_i386.deb) ...
Errno architecture (i486-linux-gnu-thread-multi-2.6.15.7) does not match executable architecture (i486-linux-gnu-thread-multi-2.6.24-14-server) at /usr/local/share/perl/5.8.8/Errno.pm line 11.
Compilation failed in require at /usr/sbin/install-info line 304.
BEGIN failed--compilation aborted at /usr/sbin/install-info line 304.
dpkg: warning - old pre-removal script returned error exit status 9
dpkg - trying script from the new package instead ...
Errno architecture (i486-linux-gnu-thread-multi-2.6.15.7) does not match executable architecture (i486-linux-gnu-thread-multi-2.6.24-14-server) at /usr/local/share/perl/5.8.8/Errno.pm line 11.
Compilation failed in require at /usr/sbin/install-info line 304.
BEGIN failed--compilation aborted at /usr/sbin/install-info line 304.
dpkg: error processing /var/cache/apt/archives/util-linux_2.13.1-5ubuntu3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 9
Errno architecture (i486-linux-gnu-thread-multi-2.6.15.7) does not match executable architecture (i486-linux-gnu-thread-multi-2.6.24-14-server) at /usr/local/share/perl/5.8.8/Errno.pm line 11.
Compilation failed in require at /usr/sbin/install-info line 304.
BEGIN failed--compilation aborted at /usr/sbin/install-info line 304.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 /var/cache/apt/archives/util-linux_2.13.1-5ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Following some earlier posts on similar problems I have verified there is only one version of install-info:

# which install-info
/usr/sbin/install-info

# dpkg -S $(which install-info)
dpkg: /usr/sbin/install-info

Where my case seems to differ from previous problems is that install-info --version throws an error:

install-info --version
Errno architecture (i486-linux-gnu-thread-multi-2.6.15.7) does not match executable architecture (i486-linux-gnu-thread-multi-2.6.24-14-server) at /usr/local/share/perl/5.8.8/Errno.pm line 11.
Compilation failed in require at /usr/sbin/install-info line 304.
BEGIN failed--compilation aborted at /usr/sbin/install-info line 304.

This is a system that was installed with LTS and not upgraded from a previous version. Perl is version 5.8.8 and installed from Ubuntu, though we do have some custom modules installed from CPAN.

I run system upgrades about once a week and this is only happening following todays update. Has anyone else got this problem?

---

### Post by alex-v on 2009-01-09
I am having the same problem with Kubuntu 8.04 as of this morning.

---

### Post by miceng on 2009-01-09
OK I submitted a bug report over at launchpad. I will post here if I hear anything.

---

### Post by zzzv on 2009-01-09
I have encountered this problem with the latest upgrade as well, also 8.04 Server.

---

### Post by jconerly on 2009-01-10
I found a quick way to deal with this.

1. Edit installed copy of Errno.pm (the path is in the error message)

```
sudo vim /usr/local/share/perl/5.8.8/Errno.pm
```

Comment out lines 11-13 (perl comments begin with the '#' pound sign), save and exit. Don't worry that you are editing an installed copy of this file; it's auto generated and we're going to blow it away in a sec.

2. Install all your Ubuntu updates

```
sudo synaptic
```

After a successful install quit synaptic.

3. Restart your machine.

4. Once logged back in check to make sure that lines 11-13 in Error.pm are still commented out or CPAN will not work. (they should still be commented out)

5. Now we need to force install Errno.pm. Errno.pm gets generated at module build time and uses a lot of your system's environment variables. The original error came about because the system 'osvers' changed but Errno.pm was not updated to reflect that. So let's blow it away and re-generated it with a fresh set of environment variables:

```
sudo cpan -f Errno
```

All should be good in the hood now.

HTH

./james

---

### Post by miceng on 2009-01-16
This fixed worked for me, though I didn't do the reboot yet as this is a prod server. There has still been no response to the bug I filed so thanks very much for the fix.

---

### Post by engnr on 2009-01-25
A reboot is not required.  I was able to avoid rebooting a production cluster by commenting the offending lines and doing `cpan -f Errno`

---

### Post by cconstantine on 2009-02-09
> **miceng said:**
> OK I submitted a bug report over at launchpad. I will post here if I hear anything.

Took me a minute to find this bug...

[https://bugs.launchpad.net/bugs/315602](https://bugs.launchpad.net/bugs/315602)

---

