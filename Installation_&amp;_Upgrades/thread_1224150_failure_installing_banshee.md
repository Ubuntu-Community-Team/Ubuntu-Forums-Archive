---
title: "failure installing banshee"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by deankovell on 2009-07-27
I started the installation of Banshee this morning, and came back to my computer 20 minutes later and the computer had froze. Later after I got off work synaptic gave me the message that dpkg was interrupted, and I ran 'sudo dpkg --configure -a' in the console. The output I get is, 

 ```
Setting up libtaglib2.0-cil (2.03.2 +dfsg-3) ...
*installing 2 assemblies from libtaglib2.0-cil into mono.
```(the output may not be exactly right as far as upper case and lower case and spaces in the right place; copy and paste wasn't working) It seems to hang there with just the flashing cursor, and other stuff quits working right. I can't start other programs or shut them off. If I move a panel around on the screen it just leaves tracers all over everything. after reboot everything else works again. banshee actually shows up in my sound and video menu. I can start the app, but it immediately crashes.  Would someone please help me finish the installation, b/c I'd like to try out the program, but if it's not going to work, how do I make it go away, so I can use synaptic to try some different audio programs. Maybe I'm not being patient enough; is 15 or 20 minutes long enough to expect it to be finished configuring?
I'm using ubuntu studio  jaunty 32-bit. 


I did finally diagnose the problem, but haven't actually solved it. If you can offer help, it might be a good idea to skip to post #9

---

### Post by directhex on 2009-07-27
How much free disk space do you have? Have you rebooted lately?

---

### Post by deankovell on 2009-07-27
I right clicked on the filesystem icon and the properties menu showed 50.9gb free space. Yes, I have rebooted. I had to shut down with the main power button after it locked up, and I've also shut it down normally a couple times since.

---

### Post by directhex on 2009-07-27
> **deankovell said:**
> I right clicked on the filesystem icon and the properties menu showed 50.9gb free space. Yes, I have rebooted. I had to shut down with the main power button after it locked up, and I've also shut it down normally a couple times since.

And does "gacutil --help" work?

---

### Post by deankovell on 2009-07-27
thanks for the help directhex.

gacutil --help gave me this. 

```

Usage: gacutil.exe <commands> [ <options> ]
Commands:
-i <assembly_path> [-check_refs] [-package NAME] [-root ROOTDIR] [-gacdir GACDIR]
    Installs an assembly into the global assembly cache.
    <assembly_path> is the name of the file that contains the     assembly manifest
    Example: -i myDll.dll

-il <assembly_list_file> [-check_refs] [-package NAME] [-root ROOTDIR] [-gacdir GACDIR]
    Installs one or more assemblies into the global assembly cache.
    <assembly_list_file> is the path to a test file containing a list of
    assembly file paths on separate lines.
    Example -il assembly_list.txt
        assembly_list.txt contents:
        assembly1.dll
        assembly2.dll

-u <assembly_display_name> [-package NAME] [-root ROOTDIR] [-gacdir GACDIR]
    Uninstalls an assembly from the global assembly cache.
    <assembly_display_name> is the name of the assembly (partial or
    fully qualified) to remove from the global assembly cache. If a 
    partial name is specified all matching assemblies will be uninstalled.
    Example: -u myDll,Version=1.2.1.0

-ul <assembly_list_file> [-package NAME] [-root ROOTDIR] [-gacdir GACDIR]
    Uninstalls one or more assemblies from the global assembly cache.
    <assembly_list_file> is the path to a test file containing a list of
    assembly names on separate lines.
    Example -ul assembly_list.txt
        assembly_list.txt contents:
        assembly1,Version=1.0.0.0,Culture=en,PublicKeyToken=0123456789abcdef
        assembly2,Version=2.0.0.0,Culture=en,PublicKeyToken=0123456789abcdef

-us <assembly_path> [-package NAME] [-root ROOTDIR] [-gacdir GACDIR]
    Uninstalls an assembly using the specifed assemblies full name.
    <assembly path> is the path to an assembly. The full assembly name
    is retrieved from the specified assembly if there is an assembly in
    the GAC with a matching name, it is removed.
    Example: -us myDll.dll

-l [assembly_name] [-root ROOTDIR] [-gacdir GACDIR]
    Lists the contents of the global assembly cache.
    When the <assembly_name> parameter is specified only matching
    assemblies are listed.

-?
    Displays a detailed help screen

Options:
-package <NAME>
    Used to create a directory in prefix/lib/mono with the name NAME, and a
    symlink is created from NAME/assembly_name to the assembly on the GAC.
    This is used so developers can reference a set of libraries at once.

-gacdir <GACDIR>
    Used to specify the GACs base directory. Once an assembly has been installed
    to a non standard gacdir the MONO_GAC_PREFIX environment variable must be used
    to access the assembly.

-root <ROOTDIR>
    Used by developers integrating this with automake tools or packaging tools
    that require a prefix directory to  be specified. The root represents the
    "libdir" component of a prefix (typically prefix/lib).

-check_refs
    Used to ensure that the assembly being installed into the GAC does not
    reference any non strong named assemblies. Assemblies being installed to
    the GAC should not reference non strong named assemblies, however the is
    an optional check.

Ignored Options:
-f
    The Mono gacutil ignores the -f option to maintain commandline compatibility with
    other gacutils. gacutil will always force the installation of a new assembly.

-r <reference_scheme> <reference_id> <description>
    The Mono gacutil has not implemented traced references and will emit a warning
    when this option is used.
```

Googling for info on this I saw you had posted on an older thread about problems with mono and GAC. is that a simmular issue?  

[http://ubuntuforums.org/showthread.php?t=640121](http://ubuntuforums.org/showthread.php?t=640121)

---

### Post by directhex on 2009-07-27
> **deankovell said:**
> thanks for the help directhex.

gacutil --help gave me this. 

```

Usage: gacutil.exe <commands> [ <options> ]
Commands:
-i <assembly_path> [-check_refs] [-package NAME] [-root ROOTDIR] [-gacdir GACDIR]
    Installs an assembly into the global assembly cache.
    <assembly_path> is the name of the file that contains the     assembly manifest
    Example: -i myDll.dll

-il <assembly_list_file> [-check_refs] [-package NAME] [-root ROOTDIR] [-gacdir GACDIR]
    Installs one or more assemblies into the global assembly cache.
    <assembly_list_file> is the path to a test file containing a list of
    assembly file paths on separate lines.
    Example -il assembly_list.txt
        assembly_list.txt contents:
        assembly1.dll
        assembly2.dll

-u <assembly_display_name> [-package NAME] [-root ROOTDIR] [-gacdir GACDIR]
    Uninstalls an assembly from the global assembly cache.
    <assembly_display_name> is the name of the assembly (partial or
    fully qualified) to remove from the global assembly cache. If a 
    partial name is specified all matching assemblies will be uninstalled.
    Example: -u myDll,Version=1.2.1.0

-ul <assembly_list_file> [-package NAME] [-root ROOTDIR] [-gacdir GACDIR]
    Uninstalls one or more assemblies from the global assembly cache.
    <assembly_list_file> is the path to a test file containing a list of
    assembly names on separate lines.
    Example -ul assembly_list.txt
        assembly_list.txt contents:
        assembly1,Version=1.0.0.0,Culture=en,PublicKeyToken=0123456789abcdef
        assembly2,Version=2.0.0.0,Culture=en,PublicKeyToken=0123456789abcdef

-us <assembly_path> [-package NAME] [-root ROOTDIR] [-gacdir GACDIR]
    Uninstalls an assembly using the specifed assemblies full name.
    <assembly path> is the path to an assembly. The full assembly name
    is retrieved from the specified assembly if there is an assembly in
    the GAC with a matching name, it is removed.
    Example: -us myDll.dll

-l [assembly_name] [-root ROOTDIR] [-gacdir GACDIR]
    Lists the contents of the global assembly cache.
    When the <assembly_name> parameter is specified only matching
    assemblies are listed.

-?
    Displays a detailed help screen

Options:
-package <NAME>
    Used to create a directory in prefix/lib/mono with the name NAME, and a
    symlink is created from NAME/assembly_name to the assembly on the GAC.
    This is used so developers can reference a set of libraries at once.

-gacdir <GACDIR>
    Used to specify the GACs base directory. Once an assembly has been installed
    to a non standard gacdir the MONO_GAC_PREFIX environment variable must be used
    to access the assembly.

-root <ROOTDIR>
    Used by developers integrating this with automake tools or packaging tools
    that require a prefix directory to  be specified. The root represents the
    "libdir" component of a prefix (typically prefix/lib).

-check_refs
    Used to ensure that the assembly being installed into the GAC does not
    reference any non strong named assemblies. Assemblies being installed to
    the GAC should not reference non strong named assemblies, however the is
    an optional check.

Ignored Options:
-f
    The Mono gacutil ignores the -f option to maintain commandline compatibility with
    other gacutils. gacutil will always force the installation of a new assembly.

-r <reference_scheme> <reference_id> <description>
    The Mono gacutil has not implemented traced references and will emit a warning
    when this option is used.
```


Hm. So Mono seems to be working fine, yet it's hanging during lib installation (which uses gacutil)? How very odd.

---

### Post by deankovell on 2009-07-27
I tried the config command again and it hung up the same way, but in a different spot. 

```
Setting up libavahil.0-cil (0.6.19-3ubuntu1) ...
*Installing 1 assembly from libavahil.0-cil

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
setting up podsleuth  (0.????) ...
setting up libbood2.0 cil (0.8.2)
```

Question marks are mine, and again some mistakes are in the code I wrote down. my pen ran out on me and I couldn't find another.

---

### Post by deankovell on 2009-07-29
Thanks again for the help directhex. I think I have a clue to what the problem is, but I don't know how to fix it.
 sudo dpkg -l | grep -v ^ii 
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                  Version                                   Description
+++-=====================================-=========================================-============================================
iU  banshee                               1.4.3-3ubuntu2                            Media Management and Playback application
rc  libavcodec52                          3:0.svn20090303-1ubuntu6                  ffmpeg codec library
rc  libavutil49                           3:0.svn20090303-1ubuntu6                  ffmpeg utility library
iU  libboo2.0-cil                         0.8.2.2960+dfsg-1                         python-like language and compiler for the CL
iU  libmono-zeroconf1.0-cil               0.7.6-1ubuntu1                            CLI library for multicast DNS service discov
```I ran this.
 I did sudo dpkg --purge remove for all of these programs, but when I tried with for libboo2.0-cil I got an error. I don't know if the openoffice stuff is really that important. I had to remove some files to get openoffice to finish installing a while back. The error at the end has an older bug posted about it, and I don't yet know how to fix it. is this probably the source of the problem?

[https://bugs.launchpad.net/ubuntu/+source/boo/+bug/293503 ]("https://bugs.launchpad.net/ubuntu/+source/boo/+bug/293503")

```
dpkg - warning: ignoring request to remove remove which isn't installed.
(Reading database ... 
dpkg: serious warning: files list file for package `openoffice.org-emailmerge' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-style-human' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-java-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-impress' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-officebean' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-base' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-math' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-core' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-draw' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-filter-mobiledev' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-writer2latex' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-calc' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-filter-binfilter' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-report-builder-bin' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-base-core' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-writer' missing, assuming package has no files currently installed.
153062 files and directories currently installed.)
Removing libboo2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.1.0.Boo.Lang.Useful.installcligac
dpkg: error processing libboo2.0-cil (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 libboo2.0-cil
```

---

### Post by deankovell on 2009-07-30
Banshee wasn't installing right because libboo2.0-cil is one of the dependencies, which wsn't installing correctly. synaptic, and dpkg wouldn't remove libboo2.0-cil because of an error: 
```
Removing libboo2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.1.0.Boo.Lang.Useful.installcligac
dpkg: error processing libboo2.0-cil (--remove):
 subprocess post-removal script returned error exit status 1

```There is a bug report over this from november of last year, but I couldn't find any fixes for it. Is there a newer version or a workaround that I haven't been able to find?
[https://bugs.launchpad.net/ubuntu/+source/boo/+bug/293503](https://bugs.launchpad.net/ubuntu/+source/boo/+bug/293503)

I ran this command: locate libboo2.0-cil
and then deleted all of the listed files at once; removing them one at a time didn't do anything. 
```
sudo rm -rf /var/cache/apt/archives/libboo2.0-cil_0.8.2.2960+dfsg-1_all.deb /var/crash/libboo2.0-cil.0.crash /var/lib/dpkg/info/libboo2.0-cil.clilibs /var/lib/dpkg/info/libboo2.0-cil.list /var/lib/dpkg/info/libboo2.0-cil.md5sums /var/lib/dpkg/info/libboo2.0-cil.postinst /var/lib/dpkg/info/libboo2.0-cil.postrm /var/lib/dpkg/info/libboo2.0-cil.prerm /var/lib/dpkg/info.bak/info/libboo2.0-cil.clilibs /var/lib/dpkg/info.bak/info/libboo2.0-cil.list /var/lib/dpkg/info.bak/info/libboo2.0-cil.md5sums /var/lib/dpkg/info.bak/info/libboo2.0-cil.postinst /var/lib/dpkg/info.bak/info/libboo2.0-cil.postrm /var/lib/dpkg/info.bak/info/libboo2.0-cil.prerm
```after this synaptic was able to remove libboo2.0-cil by using the fix broken packages option. however, the files still show up when I run the locate command. could someone please explain why removing all of them at the same time was necessary? and what do I need to do to get this package to work so I can install banshee? sorry if this is burdensome to try to explain. I am a bit of a newbie to all of this , but I'm trying to learn as much as I can. any help or clarification about what's causing the error would be awesome.

---

### Post by directhex on 2009-07-30
"locate" isn't live - it uses a saved list of files on your system, which is regenerated every now & again

to see if a package is installed, use "dpkg -l packagename"

---

### Post by deankovell on 2009-07-30
sweet,  it is actually gone

---

### Post by deankovell on 2009-11-11
I just wanted to go ahead and mark this as solved. that option wasn't there in june when I started this thread. I think the problem was with the real-time kernel I was using. Banshee installed perfectly and worked great on ubuntu regular.

---

