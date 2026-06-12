---
title: "[HOWTO] Connecting Ubuntu 12.04 LTS and Children's Learning Tablets (VTech)"
date: 2013-12-11
forum: Hardware
---

### Post by mindwarpstudios on 2013-12-11
I had this question a little while ago:
My Daughter just received a Storio 2 (VTech) [a.k.a. InnoTab 2] for her Birthday; how do I connect the device to the VTech online system to update it and install software?

With no support for Linux (Mac and Windows binaries are fully available), I attempted a number of approaches before finding a truly reliable means that works perfectly.  Please note that this is not (in my opinion) a true solution, this is a workaround.

As much as I am a fan of both projects, don't waste your time with Wine or Darling.  While I did try both and got some promising initial results; unfortunately, the final verdict was that the connection to this particular USB nand device was just a little beyond the scope of either environment.

**The Solution:** VMPlayer (Free Download from VMware.com) running WinXP and some adjustments to the Linux USB Configuration.
I am 99% sure that this technique will also work for LeapFrog Products (Leapster Explorer, LeapPad, etc.), though I haven't yet tested this hypothesis.
**As a side note: I have also successfully tested this with a GARMIN GPS device.**

[B][EDIT]
Ubuntu 13.10 uses a slightly different location in /sys for the usb ehci driver.
The following should be substituted in any script snippets in place of the similar string ending in ehci_hcd:
```
/sys/bus/pci/drivers/ehci-pci/
```[/B]

Step by Step:
1) Since we will be lobotomizing Linux's USB EHCI function, it is advisable to remove any unnecessary USB devices.
2) Download VMPlayer (Latest: 6.0)
3) Install that image of Windows XP you have kicking around.
4) Start up the VM but I wouldn't bother updating, since I never use it otherwise.
5) Install Flash Player 10.3.183.11 (Archived Versions are here: [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html))
    - Flash 11.x has an issue that causes the Learning Lodge Software to fail.
6) Install the Correct Version of the Learning Lodge Software for your device from VTech ([http://www.vtechkids.com/download/](http://www.vtechkids.com/download/))
7) Shut Down the VM and click through to "Edit Virtual Machine Settings"
8) Select "USB Controller" from the Device List and adjust "USB Compatability" to 1.1 (Default was 2.0)
9) Open a Terminal and issue the following commands:
```
cd /sys/bus/pci/drivers/ehci_hcd/
sudo sh -c 'find ./ -name "0000:00:*" -print| sed "s/\.\///">unbind'
```
10) Relaunch your new Windows XP VM.
11) Start the Learning Lodge Application and Plug in your device.
12) Profit.

One Caveat: You must reboot your Linux machine to re-enable USB 2.0 function....  I thought that was pretty ridiculous, so I wrote a couple of more generalized scripts to make my life easier, please feel free to adapt them to your needs.

Workaround Script: ~/scripts/vtechWorkaround  (Don't forget to modify references to the VM to suit your setup)
```
#! /bin/bash


if [ "$1" == "reset" ] ; then
  echo "Resetting System to Proper Functioning EHCI Configuration."
  sudo usb20-binding quiet bind
  usb20-vmware quiet enable ~/vmware/WinXP-Pro/
else
  echo "Lobotomizing the Laptop to enable Kiddie Tablet Functions"
  sudo usb20-binding quiet unbind
  usb20-vmware quiet disable ~/vmware/WinXP-Pro/
fi
```
This little script calls two others: usb20-binding and usb20-vmware to switch the USB 2.0 functioning on and off as needed.

Both usb20-binding (directly below) and usb20-vmware (scroll down further) are written to either provide a feedback for manual calls, or to act quietly.  Both have some limited error-checking built into them: please verify proper action.

USB 2.0 Binding Script: /usr/bin/usb20-binding
```
#! /bin/bash


if [ "$1" == "quiet" ] && [ "$2" == "unbind" ] ; then
  cd /sys/bus/pci/drivers/ehci_hcd/
  if [ -e 0000:00:* ] ; then
    find ./ -name "0000:00:*" -print > ~/.usb20-binding.device
    sudo sh -c 'find ./ -name "0000:00:*" -print | sed "s/\.\///" > unbind'
    exit
  else
    exit 1
  fi
fi
if [ "$1" == "quiet" ] && [ "$2" == "bind" ]; then
  if [ -e ~/.usb20-binding.device ] ; then
    cd /sys/bus/pci/drivers/ehci_hcd/
    sudo sh -c 'cat ~/.usb20-binding.device | sed "s/\.\///" > bind'
    rm ~/.usb20-binding.device
    exit
  else
    exit 1
  fi
fi


echo "USB 2.0 Automated Bind/Unbind Script"
echo "  mindwarpstudios 2013"
echo ""


if [ "$1" != "unbind" ] && [ "$1" != "bind"  ] ; then
  echo "An extremely simple script aimed at automating the removal/reattachment"
  echo "of the USB 2.0 system by performing unbind/bind of driver: ehci_hcd"
  echo ""
  echo "To be clear: this is a Workaround, not a Solution.  The intent of this"
  echo "script is to enable legacy/particularly proprietary hardware to successfully"
  echo "communicate with the system.  Script Initially written to enable kids'"
  echo "learning computers to communicate with a VMware environment to download"
  echo "programming on an otherwise unsupported Linux environment."
  echo ""
  echo "Note: it is advisable to disconnect all unnecessary USB devices before"
  echo "calling this script (and thereby defaulting everything to USB 1.1 speeds)"
  echo ""
  echo "Usage:"
  echo "  usb20-binding [quiet] <unbind|bind>"
  echo ""
  exit
fi


TEST=`lsusb | grep -i 2.0 | wc -l`


if [ "$TEST" == 0 ] ; then
  if [ "$1" == "unbind" ] ; then
    echo "ERROR: USB 2.0 system not present.  Cannot unbind.  Exiting."
    exit 1
  fi
fi


if [ "$TEST" == 1 ] ; then
  if [ "$1" == "bind" ] ; then
    echo "ERROR: USB 2.0 system already present.  Cannot bind.  Exiting."
    exit 1
  fi
fi
echo "Executing $1 process...  (may require su privileges)"


if [ "$1" == "unbind" ] ; then
  cd /sys/bus/pci/drivers/ehci_hcd/
  if [ -e 0000:00:* ] ; then
    find ./ -name "0000:00:*" -print > ~/.usb20-binding.device
    sudo sh -c 'find ./ -name "0000:00:*" -print | sed "s/\.\///" > unbind'
    echo "Processing complete."
    exit
  else
    echo "ERROR: Unbinding of USB 2.0 system failed. Device file not found."
    exit 1
  fi
fi
if [ "$1" == "bind" ]; then
  if [ -e ~/.usb20-binding.device ] ; then
    cd /sys/bus/pci/drivers/ehci_hcd/
    sudo sh -c 'cat ~/.usb20-binding.device | sed "s/\.\///" > bind'
    rm ~/.usb20-binding.device
    echo "Processing complete."
    exit
  else
    echo "ERROR: Binding of USB 2.0 system failed. Device ID cache not found."
    exit 1
  fi
fi

```
This script handles the binding and unbinding of EHCI function to the Linux USB system.  When the function is unbound, a cache file is created in the user's home directory.  This cache file is used in the binding process to reestablish the binding.  If this cache file is deleted before binding is attempted, a reboot will be required to restore EHCI function for USB (a.k.a. USB 2.0 speeds).

-----

Script for Automating Switch of USB 1.1 / 2.0 Setting for VMPlayer: /usr/bin/usb20-vmware
```
#! /bin/bash


if [ "$1" == "quiet" ] && [ "$2" == "disable" ] && [ -d "$3" ] ; then
  cd $3
  targetvmx=`find ./ -name "*.vmx" -print`
  sed -e 's/ehci\.present\ \=\ \"TRUE\"/ehci\.present\ \=\ \"FALSE\"/g' $targetvmx > $targetvmx.tmp && mv $targetvmx.tmp $targetvmx
  exit
fi
if [ "$1" == "quiet" ] && [ "$2" == "enable" ] && [ -d "$3" ] ; then
  cd $3
  targetvmx=`find ./ -name "*.vmx" -print`
  sed -e 's/ehci\.present\ \=\ \"FALSE\"/ehci\.present\ \=\ \"TRUE\"/g' $targetvmx > $targetvmx.tmp && mv $targetvmx.tmp $targetvmx
  exit
fi


echo "VMware Enable/Disable EHCI Function via VMX Edit"
echo "  mindwarpstudios 2013"
echo ""


if [ "$1" != "disable" ] && [ "$1" != "enable"  ] ; then
  echo "An extremely simple script aimed at automating enabling/disabling"
  echo "of the USB 2.0 system by removing support for EHCI in VMX file"
  echo ""
  echo "If no path to the VM is specified on the command line, this script"
  echo "will search (only) the current directory to find a VMX file.  This"
  echo "is intended as a feature to reduce automatic selection and editing"
  echo "of the wrong file."
  echo ""
  echo "Usage:"
  echo "  usb20-vmare [quiet] <disable|enable> [path to vm folder]"
  echo ""
  exit
fi


if [ -d "$2" ] ; then
  cd $2
fi
targetvmx=`find ./ -maxdepth 1 -name "*.vmx" -print`
if [ -e "$targetvmx" ] ; then
  echo -n "VMX file found: $targetvmx.  Press [Enter] to use this file."
  if read -t 3 response ; then
    echo "VMX file selected: $targetvmx."
    if [ "$1" == "disable" ] ; then
      sed -e 's/ehci\.present\ \=\ \"TRUE\"/ehci\.present\ \=\ \"FALSE\"/g' $targetvmx > $targetvmx.tmp && mv $targetvmx.tmp $targetvmx
    elif [ "$1" == "enable" ] ; then
      sed -e 's/ehci\.present\ \=\ \"FALSE\"/ehci\.present\ \=\ \"TRUE\"/g' $targetvmx > $targetvmx.tmp && mv $targetvmx.tmp $targetvmx
    else
      echo "Unrecognized Parameter.  Exiting."
      exit 1
    fi
  else
    echo ""
    echo "VMX file ignored: $targetvmx. Exiting due to User-(non)Interaction."
    exit 2
  fi
fi
echo "Processing Complete."
exit

```
This script modifies the VMX file in you VM's root folder.  Ensure that the VM is powered down prior to running this script.  This script was written and has been verified against a VMX file originally created with VMPlayer 5.x and currently used with VMPlayer 6.x.  It employs sed to locate the appropriate strings for the adjustment, though it is solid with v6.x, I cannot speak for future's newer formats and how they might break the script.

I hope someone finds this useful.


I must thank Deepak Mittal for his post: [http://www.geekdevs.com/2010/04/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/](http://www.geekdevs.com/2010/04/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/)
His post included the script I referenced in Step 9.

---

