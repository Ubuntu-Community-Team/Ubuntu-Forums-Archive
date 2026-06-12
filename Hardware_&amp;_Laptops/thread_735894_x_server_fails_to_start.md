---
title: "x server fails to start"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by BachNation on 2008-03-26
just got ati raedon x1600 pci
when i get drivers and restart
i get error:
line 47 too many arguments
any help would be greatly appreciated 

xorg_conf_failsafe=${BPX_XORG_CONF_FAILSAFE:-"/etc/X11/xorg.conf.failsafe"}
xorg_conf=${BPX_XORG_CONF:-"/etc/X11/xorg.conf"}

run_dexconf=${BPX_RUN_DEXCONF:-"yes"}

# TODO:  This should be set to "vga", however I have been unable to
#        succeed in getting the vga driver running in anything over
#        320x200, which is unusable.  So fallback is disabled for now.
#fallback_driver="vga"
fallback_driver=${BPX_FALLBACK_DRIVER:-"vesa"}

client=${BPX_CLIENT:-"/etc/gdm/failsafeXinit"}
clientargs=${BPX_CLIENTARGS:-$xorg_conf_failsafe}
blacklist=${BPX_BLACKLIST:-"/etc/gdm/failsafeBlacklist"}
main_driver=${BPX_DRIVER:-"vesa"}
checkduration=${BPX_CHECK_DURATION:-30}
failsafe_log=${BPX_LOG:-"/var/log/gdm/failsafe.log"}

server=${BPX_SERVER:-/usr/bin/X}
serverargs=${BPX_SERVERARGS:-"$*"}
if [ -z $serverargs ]; then
    # Use :10 to avoid overwriting the (failed) Xorg.0.log
    serverargs=":10"
fi
serverargs="${serverargs} -br -once -config $xorg_conf_failsafe"
   # -br:      Black background
   # -once:    Terminate server after one session
   # -config:  Specify location of xorg.conf file to use
   #           Note: Only root can specify absolute paths

warn() {
    echo "Warning:  $1" 1>&2
}

is_installed() {
    prog=$1
    need=$2
    /usr/bin/which $prog > /dev/null 2>&1
    err=$?
    if [ ! $err = 0 ]; then
	warn "Could not $need because $prog is not installed ($err)"
	return $err
    fi
    return 0
}

# Tests if the given pciids are in numerical order from least to greatest
# (e.g., $a <= $b <= $c <= ...)
pciids_in_order() {
    lastid=0
    for pciid in $* ; do
        # Strip embedded : and convert hex to dec
        id=$((0x${pciid/:/}))
        if [ $id -lt $lastid ]; then
            return 1
        fi
        lastid=$id
    done
    return 0
}

get_edid() {
    # Retrieve EDID (if get-edid is installed)
    is_installed get-edid "retrieve EDID" || return 1

    # Discard stderr, which is text data about the card
    get-edid 2>/dev/null
}

get_pciids() {
    # Retrieve PCI IDs from discover
    is_installed discover "retreive PCI IDs" || return 1

    discover --enable-all video --format="%i\n"
}

get_driver() {
    EDID=$(get_edid)
    PCIIDS=$(get_pciids)

    if [ "x$EDID" = "x" ]; then
	echo $fallback_driver
	return 1
    elif [ "x$PCIIDS" = "x" ]; then
	echo $fallback_driver
	return 2
    fi

    # TODO:  What if we have multiple pciids?  Assume first for now.
    pciid=$(echo $PCIIDS | head -n 1)

    EDID_MD5=$(echo $EDID | md5sum | head -n1 | cut -d" " -f1)
    matches=$(egrep "^$EDID_MD5|^ANY" $blacklist)
    found="no"
    for line in "$matches"; do
	line=$(echo $line | sed -e "s/ \+/ /")
	range=$(echo $line | cut -d' ' -f 2)
	driver=$(echo $line | cut -d' ' -f 3)
	pciid1=$(echo $range | cut -d- -f 1)
	pciid2=$(echo $range | cut -d- -f 2)

	if [ "x$pciid1" = "x" ]; then
            continue
	elif [ "x$pciid1" = "xANY" ]; then
	    found="yes"
	    break
	elif [ "$pciid1" = "$pciid" ]; then
	    found="yes"
	    break
	elif [ "x$pciid2" = "x" ]; then
            continue
	elif pciids_in_order $pciid1 $pciid $pciid2 ; then
	    found="yes"
	    break
	fi
    done

    if [ $found = "no" ]; then
	echo $main_driver

    else
	# No driver was specified - assume vga
	if [ "x$driver" = "x" ]; then
	    warn "System is blacklisted, but no driver specified; assuming fallback"
	    driver=$fallback_driver
	fi

	echo $driver
    fi

    return 0
}

# Check if we've already attempted a failsafe session without success
if [ -e "$failsafe_log" ]; then
    cur_time=$(date +"%s")
    last_run=$(tail -n 1 $failsafe_log | cut -d' ' -f1)
    time_diff=$(expr $cur_time - $last_run)
    if [ $time_diff -lt $checkduration ]; then
        warn "Failsafe mode was already attempted within $checkduration seconds."
        warn "Falling back to gdm to report the issue."
        exit 1
    fi
fi

# When failsafe mode is activated, check the blacklist for systems we
# know do not support VESA 800x600/256
#      Use EDID + PCI IDs as key to lookup (Can get PCI IDs from discover)
#      If the display does not give EDID info, then use VGA 640x480/16 mode
#      If a matching entry is found, then use VGA 640x480/16 mode
driver=$(get_driver)

if [ "x${run_dexconf}" = "xyes" ]; then
    # Generate an appropriate xorg.conf
    /etc/gdm/failsafeDexconf $driver $xorg_conf_failsafe
    if [ ! -s $xorg_conf_failsafe ]; then
        warn "Could not generate $xorg_conf_failsafe for $driver driver"
        exit 1
    fi
elif [ ! -s $xorg_conf_failsafe ]; then
    warn "Requested to use $xorg_conf_failsafe for $driver driver, but it does not exist"
    exit 1
fi

md5xorg=$(md5sum $xorg_conf)
date +"%s $md5xorg" >> $failsafe_log
if [ $? -ne 0 ]; then
    warn "Cannot write to $failsafe_log"
fi

# TODO:  Start up the failsafe X session using their regular user account

if pidof /usr/sbin/gdm ; then
    clientargs="${clientargs} with-gdm"
fi

echo "xinit $client $clientargs -- $server $serverargs"
xinit $client $clientargs -- $server $serverargs &

sleep 3

# Stop gdm if it's running, otherwise it will attempt to manage the display
# out from under us
if pidof /usr/sbin/gdm ; then
    exec kill -STOP $PPID
fi

# This seems to cause gdm to attempt to start a new x session
#exec kill -USR1 `cat /var/run/gdm.pid`

---

### Post by Vermind on 2008-03-26
Hello,
What exactly do You refer to with "get drivers"?
What is this code You pasted in the post?

When I last installed ATI drivers from the official installer, I first ran
```
sudo umount /lib/modules/`uname -r`/volatile
``` in order to get the ATI driver to stick instead of it going to the tmpfs of the restricted drivers of Ubuntu.

Can You start X normally with ```
sudo killall -s TERM Xorg X gdm; sudo gdm
```?

It would also be useful to know Your Ubuntu flavor and see Your /etc/X11/xorg.conf. If You did not use the official fglrx driver in xorg.conf before, then in order to get 3D acceleration working (and for newer cards even X) You need to change the "radeon" or "ati" there to "fglrx".

---

