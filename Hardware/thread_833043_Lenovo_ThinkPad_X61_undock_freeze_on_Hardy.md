---
title: "Lenovo ThinkPad X61 undock freeze on Hardy"
date: 2008-06-18
forum: Hardware
---

### Post by zivleyes on 2008-06-18
I know a lot of people have this problem and I'm happy to share with you the solution I've found for this.
I've installed the 64Bit version of Ubuntu Ultimate 1.8 (it's basically a customized Ubuntu 8.04 Hardy) on my Lenovo X61 Laptop and had the same problem, all my other ThinkPad Buttons worked out of the box (Except the blue one which I don't care for) but I couldn't get the dock/undock to work, every time I tried the computer froze, so after a whole day searching I've found that it's a known bug that will be probably addressed in a future kernel patch or something like that, but I didn't give up and kept searching.
I've found this info in ThinkWiki: [http://www.thinkwiki.org/wiki/UltraBase_X6](http://www.thinkwiki.org/wiki/UltraBase_X6)

Based on this, I've made up my solution, here it is:

First of all you need to be sure your thinkpad_acpi module is loaded
```
lsmod | grep thinkpad
```
You should get something like this:
```

thinkpad_acpi          60304  0 
nvram                  11400  2 thinkpad_acpi

```
If not, then load it
```
sudo modprobe thinkpad_acpi
```

Now, you need to get the latest version of "Dockutils" from the OpenSuse repos (someone here to host a .deb package?)
I've got this one, the current one that matches my machine:
[http://download.opensuse.org/distribution/openSUSE-current/repo/oss/suse/x86_64/dockutils-0.2-21.x86_64.rpm?mirrorlist](http://download.opensuse.org/distribution/openSUSE-current/repo/oss/suse/x86_64/dockutils-0.2-21.x86_64.rpm?mirrorlist)
But you may need to browse a bit to find a version that suits you.
Because we're using RPM package, you need to install alien if you don't have it already
```
sudo apt-get install alien
```
Then convert the RPM to DEB and install it with:
```
sudo alien -i dockutils-0.2-21.x86_64.rpm
```

Now we need to follow the explanations given by ThinkWiki page:

In order to have the docking handled automatically, we need to create a hook in Dockutils directory(/usr/lib/dockutils). We will put our hook in hooks/thinkpad/ directory. 
Create this new file
```
sudo vi /usr/lib/dockutils/hooks/thinkpad/70x61
```
and paste this text
```

#!/bin/bash
# dock/undock script for Thinkpad X61

export DISPLAY=:0

if [ "$1" = "dock" ]; then
        echo "X61 dock"
        # non-present dvd drive workaround
        /bin/rescan-scsi-bus.sh --hosts=1 --channels=0 --ids=0 --luns=0 --forceremove &

        # set external display resolution & dpi
        /usr/bin/xrandr --output VGA --auto
        /usr/bin/xrandr --screen 0 -s 1920x1200
        /usr/bin/xrandr --screen 0 --dpi 96x96

elif [ "$1" = "undock" ]; then
        echo "X61 undock"

        # turn external display off, internal on and set res
        /usr/bin/xrandr --screen 0 -s 1024x768
        /usr/bin/xrandr --output LVDS --auto
        /usr/bin/xrandr --output VGA --off
        /usr/bin/xrandr --screen 0 --dpi 96x96
fi

```
NOTE!
If you don't use external display when docked, remove/comment out the /usr/bin/xrandr lines from the script.

ou can always run the Dockutils using # docker dock or # docker undock command, but this is not comfortable. We will use the ACPI subsystem to bind FnF8, FnF9 keys and side button on the docking station to the Dockutils. This could be performed using the following codes. Create the files and paste the codes.
On this file
```
vi /etc/acpi/events/dock
```
paste this:
```

event=(ibm/dock GDCK 00000000 00000003|ibm/hotkey HKEY 00000080 00001008)
action=/usr/sbin/docker dock

```
On this one
```
vi /etc/acpi/events/undock
```
paste this:
```

event=(ibm/dock GDCK 00000003 00000001|ibm/hotkey HKEY 00000080 00001009)
action=/usr/sbin/docker undock

```
Now, you should be able to undock your PC using the keyboard keys and the dock button.
NOTE!
thinkpad_acpi and acpid must be installed and running for this to work

THANKS A LOT TO THINKWIKI GUYS FOR SAVING ME!!!

Hope I helped someone else too!

Enjoy,
Ziv

---

### Post by zivley on 2008-06-24
I just wanted to add that there might be another little issue with the use of dockutils, if you manually run the command ```
/usr/sbin/docker undock
``` you may get this error:
```

error: libhal_device_get_property_type: org.freedesktop.Hal.NoSuchProperty:
No property smbios.system.version on device with id /org/freedesktop/Hal/devices/computer
Sat Apr 12 11:57:49 CEST 2008: running misc hooks for event undock.

```
In order to solve this you need to edit the file /usr/lib/dockutils/dockhandler and and replace "smbios.system.version" with "system.hardware.version"

Also, if the button on the docking station doesn't work, a simple "modprobe dock" command will fix it.

And of course I've found that the "dock" action tries to solve a problem with the re-detection of the CD/DVD driver by running a script that doesn't exist by default, so here it is, create a new file /bin/rescan-scsi-bus.sh and paste this:
```

#!/bin/bash
# Skript to rescan SCSI bus, using the 
# scsi add-single-device mechanism
# (w) 1998-03-19 Kurt Garloff <kurt@garloff.de> (c) GNU GPL
# (w) 2003-07-16 Kurt Garloff <garloff@suse.de> (c) GNU GPL
# $Id: rescan-scsi-bus.sh,v 1.25 2007/07/18 23:14:04 garloff Exp $

setcolor ()
{
  red="\e[0;31m"
  green="\e[0;32m"
  yellow="\e[0;33m"
  bold="\e[0;1m"
  norm="\e[0;0m"
}

unsetcolor () 
{
  red=""; green=""
  yellow=""; norm=""
}

# Return hosts. sysfs must be mounted
findhosts_26 ()
{
  hosts=
  if ! ls /sys/class/scsi_host/host* >/dev/null 2>&1; then
    echo "No SCSI host adapters found in sysfs"
    exit 1;
  fi 
  for hostdir in /sys/class/scsi_host/host*; do
    hostno=${hostdir#/sys/class/scsi_host/host}
    if [ -f $hostdir/isp_name ] ; then
	hostname="qla2xxx"
    elif [ -f $hostdir/lpfc_drvr_version ] ; then
	hostname="lpfc"
    else
        hostname=`cat $hostdir/proc_name`
    fi
    hosts="$hosts $hostno"
    echo "Host adapter $hostno ($hostname) found."
  done  
}

# Return hosts. /proc/scsi/HOSTADAPTER/? must exist
findhosts ()
{
  hosts=
  for driverdir in /proc/scsi/*; do
    driver=${driverdir#/proc/scsi/}
    if test $driver = scsi -o $driver = sg -o $driver = dummy -o $driver = device_info; then continue; fi
    for hostdir in $driverdir/*; do
      name=${hostdir#/proc/scsi/*/}
      if test $name = add_map -o $name = map -o $name = mod_parm; then continue; fi
      num=$name
      driverinfo=$driver
      if test -r $hostdir/status; then
	num=$(printf '%d\n' `sed -n 's/SCSI host number://p' $hostdir/status`)
	driverinfo="$driver:$name"
      fi
      hosts="$hosts $num"
      echo "Host adapter $num ($driverinfo) found."
    done
  done
}

# Get /proc/scsi/scsi info for device $host:$channel:$id:$lun
# Optional parameter: Number of lines after first (default = 2), 
# result in SCSISTR, return code 1 means empty.
procscsiscsi ()
{  
  if test -z "$1"; then LN=2; else LN=$1; fi
  CHANNEL=`printf "%02i" $channel`
  ID=`printf "%02i" $id`
  LUN=`printf "%02i" $lun`
  if [ -d /sys/class/scsi_device ]; then
      SCSIPATH="/sys/class/scsi_device/${host}:${channel}:${id}:${lun}"
      if [ -d  "$SCSIPATH" ] ; then
	  SCSISTR="Host: scsi${host} Channel: $CHANNEL Id: $ID Lun: $LUN"
	  if [ "$LN" -gt 0 ] ; then
	      IVEND=$(cat ${SCSIPATH}/device/vendor)
	      IPROD=$(cat ${SCSIPATH}/device/model)
	      IPREV=$(cat ${SCSIPATH}/device/rev)
	      SCSIDEV=$(printf '  Vendor: %-08s Model: %-16s Rev: %-4s' "$IVEND" "$IPROD" "$IPREV")
	      SCSISTR="$SCSISTR
$SCSIDEV"
	  fi
	  if [ "$LN" -gt 1 ] ; then
	      ILVL=$(cat ${SCSIPATH}/device/scsi_level)
	      type=$(cat ${SCSIPATH}/device/type)
	      case "$type" in
		  0) ITYPE="Direct-Access    " ;;
		  1) ITYPE="Sequential-Access" ;;
		  2) ITYPE="Printer          " ;;
		  3) ITYPE="Processor        " ;;
		  4) ITYPE="WORM             " ;;
		  5) ITYPE="CD-ROM           " ;;
		  6) ITYPE="Scanner          " ;;
		  7) ITYPE="Optical Device   " ;;
		  8) ITYPE="Medium Changer   " ;;
		  9) ITYPE="Communications   " ;;
		  10) ITYPE="Unknown          " ;;
		  11) ITYPE="Unknown          " ;;
		  12) ITYPE="RAID             " ;;
		  13) ITYPE="Enclosure        " ;;
		  14) ITYPE="Direct-Access-RBC" ;;
		  *) ITYPE="Unknown          " ;;
	      esac
	      SCSITMP=$(printf '  Type:   %-16s                ANSI SCSI revision: %02d' "$ITYPE" "$((ILVL - 1))")
	      SCSISTR="$SCSISTR
$SCSITMP"
	  fi
	      
      else
	  return 1
      fi
  else
      grepstr="scsi$host Channel: $CHANNEL Id: $ID Lun: $LUN"
      SCSISTR=`cat /proc/scsi/scsi | grep -A$LN -e"$grepstr"`
  fi
  if test -z "$SCSISTR"; then return 1; else return 0; fi
}

# Find sg device with 2.6 sysfs support
sgdevice26 ()
{
  if test -e /sys/class/scsi_device/$host\:$channel\:$id\:$lun/device/generic; then	
    SGDEV=`readlink /sys/class/scsi_device/$host\:$channel\:$id\:$lun/device/generic`
    SGDEV=`basename $SGDEV`
  else
    for SGDEV in /sys/class/scsi_generic/sg*; do
      DEV=`readlink $SGDEV/device`
      if test "${DEV##*/}" = "$host:$channel:$id:$lun"; then
	SGDEV=`basename $SGDEV`; return
      fi
    done
    SGDEV=""
  fi  
}

# Find sg device with 2.4 report-devs extensions
sgdevice24 ()
{
  if procscsiscsi 3; then
    SGDEV=`echo "$SCSISTR" | grep 'Attached drivers:' | sed 's/^ *Attached drivers: \(sg[0-9]*\).*/\1/'`
  fi
}

# Find sg device that belongs to SCSI device $host $channel $id $lun
sgdevice ()
{
  SGDEV=
  if test -d /sys/class/scsi_device; then
    sgdevice26
  else  
    DRV=`grep 'Attached drivers:' /proc/scsi/scsi 2>/dev/null`
    repdevstat=$((1-$?))
    if [ $repdevstat = 0 ]; then
      echo "scsi report-devs 1" >/proc/scsi/scsi
      DRV=`grep 'Attached drivers:' /proc/scsi/scsi 2>/dev/null`
      if [ $? = 1 ]; then return; fi
    fi
    if ! `echo $DRV | grep 'drivers: sg' >/dev/null`; then
      modprobe sg
    fi
    sgdevice24
    if [ $repdevstat = 0 ]; then
      echo "scsi report-devs 0" >/proc/scsi/scsi
    fi
  fi
}       

# Test if SCSI device is still responding to commands
testonline ()
{
  : testonline
  if test ! -x /usr/bin/sg_turs; then return 0; fi
  sgdevice
  if test -z "$SGDEV"; then return 0; fi
  sg_turs /dev/$SGDEV >/dev/null 2>&1
  RC=$?
  # echo -e "\e[A\e[A\e[A${yellow}Test existence of $SGDEV = $RC ${norm} \n\n\n"
  if test $RC = 1; then return $RC; fi
  # OK, device online, compare INQUIRY string
  INQ=`sg_inq -36 /dev/$SGDEV`
  IVEND=`echo "$INQ" | grep 'Vendor identification:' | sed 's/^[^:]*: \(.*\)$/\1/'`
  IPROD=`echo "$INQ" | grep 'Product identification:' | sed 's/^[^:]*: \(.*\)$/\1/'`
  IPREV=`echo "$INQ" | grep 'Product revision level:' | sed 's/^[^:]*: \(.*\)$/\1/'`
  STR=`printf "  Vendor: %-08s Model: %-16s Rev: %-4s" "$IVEND" "$IPROD" "$IPREV"`
  procscsiscsi
  SCSISTR=`echo "$SCSISTR" | grep 'Vendor:'`
  if [ "$SCSISTR" != "$STR" ]; then
    echo -e "\e[A\e[A\e[A\e[A${red}$SGDEV changed: ${bold}\nfrom:${SCSISTR#* } \nto: $STR ${norm}\n\n\n"
    return 1
  fi
  return $RC
}

# Test if SCSI device $host $channen $id $lun exists
# Outputs description from /proc/scsi/scsi, returns SCSISTR 
testexist ()
{
  : testexist
  SCSISTR=
  if procscsiscsi; then
    echo "$SCSISTR" | head -n1
    echo "$SCSISTR" | tail -n2 | pr -o4 -l1
  fi
}

# Returns the list of existing channels per host
chanlist ()
{
  local hcil
  local cil
  local chan
  local tmpchan

  for dev in /sys/class/scsi_device/${host}:* ; do
    hcil=${dev##*/}
    cil=${hcil#*:}
    chan=${cil%%:*}
    for tmpchan in $channelsearch ; do
      if test "$chan" -eq $tmpchan ; then
	chan=
      fi
    done
    if test -n "$chan" ; then
      channelsearch="$channelsearch $chan"
    fi
  done
}

# Returns the list of existing targets per host
idlist ()
{
  local hcil
  local cil
  local il
  local target
  local tmpid

  for dev in /sys/class/scsi_device/${host}:${channel}:* ; do
    hcil=${dev##*/}
    cil=${hcil#*:}
    il=${cil#*:}
    target=${il%%:*}
    for tmpid in $idsearch ; do
      if test "$target" -eq $tmpid ; then
	target=
      fi
    done
    if test -n "$target" ; then
      idsearch="$idsearch $target"
    fi
  done
}

# Returns the list of existing LUNs
getluns ()
{
  if test ! -x /usr/bin/sg_luns; then return ""; fi
  sgdevice
  if test -z "$SGDEV"; then return ""; fi
  sg_luns -d /dev/$SGDEV | sed -n 's/.*lun=\(.*\)/\1/p'
}

# Perform scan on a single lun
dolunscan()
{
  SCSISTR=
  devnr="$host $channel $id $lun"
  echo "Scanning for device $devnr ..."
  printf "${yellow}OLD: $norm"
  testexist
  : f $remove s $SCSISTR
  if test "$remove" -a "$SCSISTR"; then
    # Device exists: Test whether it's still online
    # (testonline returns 1 if it's gone or has changed)
    testonline
    if test $? = 1 -o ! -z "$forceremove"; then
      echo -en "\r\e[A\e[A\e[A${red}REM: "
      echo "$SCSISTR" | head -n1
      echo -e "${norm}\e[B\e[B"
      if test -e /sys/class/scsi_device/${host}:${channel}:${id}:${lun}/device; then
        echo 1 > /sys/class/scsi_device/${host}:${channel}:${id}:${lun}/device/delete
        # Try reading, should fail if device is gone
        echo "$channel $id $lun" > /sys/class/scsi_host/host${host}/scan
      else
        echo "scsi remove-single-device $devnr" > /proc/scsi/scsi
        # Try reading, should fail if device is gone
        echo "scsi add-single-device $devnr" > /proc/scsi/scsi
      fi
    fi
    printf "\r\x1b[A\x1b[A\x1b[A${yellow}OLD: $norm"
    testexist
    if test -z "$SCSISTR"; then
      printf "\r${red}DEL: $norm\r\n\n"
      let rmvd+=1;
    fi
  fi
  if test -z "$SCSISTR"; then
    # Device does not exist, try to add
    printf "\r${green}NEW: $norm"
    if test -e /sys/class/scsi_host/host${host}/scan; then
      echo "$channel $id $lun" > /sys/class/scsi_host/host${host}/scan 2> /dev/null
    else
      echo "scsi add-single-device $devnr" > /proc/scsi/scsi
    fi
    testexist
    if test -z "$SCSISTR"; then
      # Device not present
      printf "\r\x1b[A";
      # Optimization: if lun==0, stop here (only if in non-remove mode)
      if test $lun = 0 -a -z "$remove" -a $optscan = 1; then 
        break;
      fi
    else 
      let found+=1; 
    fi
  fi
}

# Perform report lun scan
doreportlun()
{
  lun=0
  SCSISTR=
  devnr="$host $channel $id $lun"
  echo "Scanning for device $devnr ..."
  printf "${yellow}OLD: $norm"
  testexist
  if test -z "$SCSISTR"; then
    # Device does not exist, try to add
    printf "\r${green}NEW: $norm"
    if test -e /sys/class/scsi_host/host${host}/scan; then
      echo "$channel $id $lun" > /sys/class/scsi_host/host${host}/scan 2> /dev/null
    else
      echo "scsi add-single-device $devnr" > /proc/scsi/scsi
    fi
    testexist
    if test -z "$SCSISTR"; then
      # Device not present
      printf "\r\x1b[A";
      lunsearch=
      return
    fi
  fi
  lunsearch=`getluns`
  lunremove=
  # Check existing luns
  for dev in /sys/class/scsi_device/$host\:$channel\:$id\:*; do
    lun=${dev##*:}
    newsearch=
    oldsearch="$lunsearch"
    for tmplun in $lunsearch; do
      if test $tmplun -eq $lun ; then
	# Optimization: don't scan lun 0 again
	if [ $lun -ne 0 ]; then
	  dolunscan
	fi
      else
	newsearch="$newsearch $tmplun"
      fi
    done
    if [ "${#oldsearch}" = "${#newsearch}" ] ; then
	# Stale lun
	lunremove="$lunremove $lun"
    fi
    lunsearch="$newsearch"
  done
  # Add new ones and check stale ones
  for lun in $lunsearch $lunremove; do
    dolunscan
  done
}
  
# Perform search (scan $host)
dosearch ()
{
  if test -z "$channelsearch" ; then
    chanlist
  fi
  for channel in $channelsearch; do
    if test -z "$idsearch" ; then
      idlist
    fi
    for id in $idsearch; do
      if test -z $lunsearch ; then
	doreportlun
      else
	for lun in $lunsearch; do
          dolunscan
        done
      fi
    done
  done
}
 
# main
if test @$1 = @--help -o @$1 = @-h -o @$1 = @-?; then
    echo "Usage: rescan-scsi-bus.sh [options] [host [host ...]]"
    echo "Options:"
    echo " -l      activates scanning for LUNs 0-7    [default: 0]"
    echo " -L NUM  activates scanning for LUNs 0--NUM [default: 0]"
    echo " -w      scan for target device IDs 0 .. 15 [default: 0-7]"
    echo " -c      enables scanning of channels 0 1   [default: 0]"
    echo " -r      enables removing of devices        [default: disabled]"
    echo " -i      issue a FibreChannel LIP reset     [default: disabled]"
    echo "--remove:        same as -r"
    echo "--issue-lip:     same as -i"
    echo "--forceremove:   Remove and readd every device (DANGEROUS)"
    echo "--nooptscan:     don't stop looking for LUNs is 0 is not found"
    echo "--color:         use coloured prefixes OLD/NEW/DEL"
    echo "--hosts=LIST:    Scan only host(s) in LIST"
    echo "--channels=LIST: Scan only channel(s) in LIST"
    echo "--ids=LIST:      Scan only target ID(s) in LIST"
    echo "--luns=LIST:     Scan only lun(s) in LIST"  
    echo " Host numbers may thus be specified either directly on cmd line (deprecated) or"
    echo " or with the --hosts=LIST parameter (recommended)."
    echo "LIST: A[-B][,C[-D]]... is a comma separated list of single values and ranges"
    echo " (No spaces allowed.)"
    exit 0
fi

expandlist ()
{
    list=$1
    result=""
    first=${list%%,*}
    rest=${list#*,}
    while test ! -z "$first"; do 
	beg=${first%%-*};
	if test "$beg" = "$first"; then
	    result="$result $beg";
    	else
    	    end=${first#*-}
	    result="$result `seq $beg $end`"
	fi
	test "$rest" = "$first" && rest=""
	first=${rest%%,*}
	rest=${rest#*,}
    done
    echo $result
}

if test ! -d /proc/scsi/; then
  echo "Error: SCSI subsystem not active"
  exit 1
fi	

# Make sure sg is there
modprobe sg >/dev/null 2>&1

# defaults
unsetcolor
lunsearch=""
idsearch=`seq 0 7`
channelsearch="0"
remove=
forceremove=
optscan=1
if test -d /sys/class/scsi_host; then 
  findhosts_26
else  
  findhosts
fi  

# Scan options
opt="$1"
while test ! -z "$opt" -a -z "${opt##-*}"; do
  opt=${opt#-}
  case "$opt" in
    l) lunsearch=`seq 0 7` ;;
    L) lunsearch=`seq 0 $2`; shift ;;
    w) idsearch=`seq 0 15` ;;
    c) channelsearch="0 1" ;;
    r) remove=1 ;;
    i) lipreset=1 ;;
    -remove)      remove=1 ;;
    -forceremove) remove=1; forceremove=1 ;;
    -hosts=*)     arg=${opt#-hosts=};   hosts=`expandlist $arg` ;;
    -channels=*)  arg=${opt#-channels=};channelsearch=`expandlist $arg` ;; 
    -ids=*)   arg=${opt#-ids=};         idsearch=`expandlist $arg` ;; 
    -luns=*)  arg=${opt#-luns=};        lunsearch=`expandlist $arg` ;; 
    -color) setcolor ;;
    -nooptscan) optscan=0 ;;
    -issue-lip) lipreset=1 ;;
    *) echo "Unknown option -$opt !" ;;
  esac
  shift
  opt="$1"
done    

# Hosts given ?
if test "@$1" != "@"; then 
  hosts=$*; 
fi

echo "Scanning SCSI subsystem for new devices"
test -z "$remove" || echo " and remove devices that have disappeared"
declare -i found=0
declare -i rmvd=0
for host in $hosts; do
  echo -n "Scanning host $host "
  if test -e /sys/class/fc_host/host$host ; then
    # It's pointless to do a target scan on FC
    if test -n "$lipreset" ; then
      echo 1 > /sys/class/fc_host/host$host/issue_lip 2> /dev/null;
      echo "- - -" > /sys/class/scsi_host/host$host/scan 2> /dev/null;
    fi
    channelsearch=""
    idsearch=""
  fi
  [ -n "$channelsearch" ] && echo -n "channels $channelsearch "
  echo -n "for "
  if [ -n "$idsearch" ] ; then
      echo -n " SCSI target IDs " $idsearch
  else
      echo -n " all SCSI target IDs"
  fi
  if [ -n "$lunsearch" ] ; then
      echo ", LUNs " $lunsearch
  else
      echo ", all LUNs"
  fi
  dosearch; 
done
echo "$found new device(s) found.               "
echo "$rmvd device(s) removed.                 "

```
Save and exit, then "chmod a+x /bin/rescan-scsi-bus.sh" and you're done.

Enjoy!
Ziv

---

