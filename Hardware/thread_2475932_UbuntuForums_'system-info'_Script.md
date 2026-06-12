---
title: "UbuntuForums 'system-info' Script"
date: 2022-02-23
forum: Hardware
---

### Post by MAFoElffen on 2022-02-23
**General**
The Ubuntu Forums "system-info" script queries the users computer and   prepares a hardware and system configuration report, so that users &   helpers can see details of your system.

**Details**
[LIST]
[*]Creates the file `system-info.txt` at the base of the user's home directory.
[*]Sanitizes, masks all sensitive info, like IP addresses, MAC addresses, Full FQDN and Serial numbers, automatically in a meaningful way.
[*]The script displays the unmasked report results within the  'less'  utility to review the results, one screen at a time. To navigate  from  there, press the space bar, left, right, up, down, page up or  page down  keys to navigate. If in a graphical terminal session, you can  also use  mouse navigation. Press the "q" key to exit "less" and  continue. It will  print the final report and offer to upload to  pastebin site.
[*]Offers to post the results to the Ubuntu `pastebinit`   provider if that program is installed, and a sufficiently reliable   internet connection is available. This is the easiest way to share the   sanitized results with the Ubuntu Community for support. It has 3 other   fallback methods to upload the pastebin of 'pastebinit' is not installed,  using either 'curl', 'wget', or netcat ('nc')  After successful upload to the  pastebin, it will both display and log  the URL of the uploaded report  (`~/system-info-link.log`), for you to  copy and paste in your post on  the Ubuntu Forums. (See note on missing  programs below.)
[*]If not uploaded to a Pastebin, if the 'system-info.txt'  report exceeds 19.5 kB in size, it will offer to create the archive  `system-info.tar.gz` for you to be able to add as an attachment to a  Forum Post.
[/LIST]

You can download and run the script using either the GUI desktop, or from the command line (Console or Terminal Session). Use whichever method you are more comfortable with.

**Download and Run from GUI Desktop**

[LIST=1]
[*]Download the [Script]("https://github.com/UbuntuForums/system-info/raw/main/system-info"). In a web browser, you can right click on the link to the left, then "Save Link As".
[*]In Nautilus or another file browser, from File Properties, Permissions, Make it executable. In File Browser, right-click on the file to get to File Properties.
[*]Run it from your file browser or a Run dialog from kdialog
[/LIST]

**Download and Run from CLI (Console or Terminal Session)**

You have a choice of either downloading the script from Github, or by adding a PPA and installing a .deb package. Please note that the command to run the script is slightly different for the two download methods.

[indent]**Download from Github:**
```

 wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
 chmod +x system-info && \
 ./system-info <options>

```
This will download the script, make it executable, and run it, all in a row (one process).

For options, see below.[/indent]

[indent]**Download from PPA**

 The UbuntuForums 'system-info' Script is now available to install as a .deb package from its PPA at: [https://launchpad.net/~mafoelffen/+archive/ubuntu/system-info](https://launchpad.net/~mafoelffen/+archive/ubuntu/system-info)
 
You can add this PPA to your system and install the package with:
 ```

    sudo add-apt-repository ppa:mafoelffen/system-info
    sudo apt update
    sudo apt install system-info
    system-info <options>

```
This Debian Installer installs the script in the Path, so you do not need to add a "path to" before the "system-info" command to start the script. 

For options, see below.[/indent]


**Usage**

The script will check to ensure you are not running as "root", as some questions need to get information of the logged in user. As some commands need elevated permissions to gather information, it will ask the user for their password to do that, where the logged in User will need to be part of the sudoer group (an Administrative User).

Various options can be invoked if the script is run from the CLI. These are optional and not needed to run the script. Normal usage is without any options.

```

Options:
    (no options)  Normal run of script is without a startup option.
    -v              Returns Version Information and exits."
    -h or --help    Displays the Help Screen, then exits."
    -s # or --show  #  Changes Verbosity levels of the logger."
            # range 0 through 5"
            Example: system-info -s 5  turns on debugging messages"
    -d or --details Displays more details to Report
        Adds more details to GPU,Storage Controller, Sound devices, 
            and ZFS (if installed).
    -r or --refresh Update script to latest version.

```

The Version of and Script Date is important to track which version or update of the script was run.


**A Note On The Message of Suggested 'Missing Programs':**
This script checks if your system has some basic Linux utilities   installed. If you do not have some of those utilities, the script can   still continue without them. For instance:
[LIST]
[*] 'pastebinit'  is useful to upload reports to paste.ubuntu.com, but this  script has 3  other fallback routines to upload this report to a  pastebin, using  other common Linux Utilities that are usually installed  by default, on  all flavors and in other distributions.
[*]'mokutil'  is not a default installed utility on computers  that are not booting as  UEFI. But it will show if the computer is UEFI  capable, and was just  installed/booted as Legacy BIOS/CSM. This utility  can also show that a  BIOS is not UEFI capable, with no harm. It is  considered as optional if  not installed, but may give you more options,  if those possibilities are known..
[*]'ubuntu-drivers'  is optional. In this script, it will show  if a computer is considered  safe to install the Hardware Enablement  Stack (HWE). This is not  something that is installed as a default  (especially on Server Editions)  but it is useful to know that  information if that is something that  might help resolve a hardware  problem on your computer, where installing the HWE may help.
[*]Etc...
[/LIST]
 
**Purpose**
I dedicated this script to the Members of Ubuntu Forums that are  involved with Community Support. Many times, while trying to provide  support, we have to ask users about their system, their hardware, and  their system settings. Initially, we do of know the skill sets of the  Users posting for help. Many users, do not know the nuts and bolts  underneath. Many times, us helpers have asked the same, common   questions to Users for many years. I created this tool to automatically  answer those questions and make it easy for a new user to easily provide  it, in a safe, sanitized format.

This script is very useful for Users to see the details of their  computer and may help them to resolve their own issues or to make plans  for upgrades. For example, it has sections that may help with hardware  inventory, for how their system sees it. It has a section on manually  installed software, which is helpful to plan migrations.

**Repository Information:**
STABLE Repository: [GitHub - UbuntuForums - system-info]("https://github.com/UbuntuForums/system-info")
DEV/TEST Repository: [GitHub - Mafoelffen1 - system-info]("https://github.com/Mafoelffen1/system-info") 

**Reviews**
The Headline story about the script from [DistroWatch Weekly 955, "Ubuntu gets new tool to gather system information."]("https://distrowatch.com/dwres.php?resource=showheadline&story=14292"), 
> 
One of the hardest aspects of reporting a bug (and helping people who    have reported problems) is knowing what information is relevant. Trying    to figure out why a computer is slow or why an operating system is    crashing can take people working on the problem down a series of paths.    One tool which is designed to help this process is the [UbuntuForums system-info]("https://github.com/UbuntuForums/system-info") script. This script gathers system information from a variety of sources and offers to upload the results to [Pastebin]("https://pastebin.com/") as well as saving the results in the user's home directory. While the script is designed to work on [Ubuntu]("https://distrowatch.com/ubuntu"), it can also function on most other mainstream distributions, such as [Fedora]("https://distrowatch.com/fedora"), with only a few gaps appearing in the information.                                

Yes, it did mention that it works with other Distributions. While  writing this, I had a very dedicated team of testers who pushed me. We  made sure it ran on both Ubuntu Desktop and Server Editions, other  flavors of Ubuntu, derivatives of Ubuntu, Debian Branch, as well as  RHEL, CentOS, Fedora, SUSE, Oracle EL, etc. I wanted to ensure it might  be of help to all Linux Users.

This script can be run locally on an installed system, run from a  LiveCD, or run remotely through a SSH Connection, VNC or XRDP session.  For remote use, the script just needs to be located on, and run on the  target device.

**Future plans:**
I will continue to try to improve this script and the report it  generates. I will add features that are useful to this Report from other  scripting in the Ama-Gi Project.

If you notice a problem or bug, please report it the DEV/TEST GitHub Issues Tracker at: [https://github.com/Mafoelffen1/system-info/issues](https://github.com/Mafoelffen1/system-info/issues), on the Development thread on this forum ([Inspired]("https://ubuntuforums.org/showthread.php?t=2465764")),  or contact me with it. If there is a problem with it on any hardware or  system, I want to hear about it so it can be resolved. 

If you have an idea for improvement, or would like a feature added, contact me.

---

