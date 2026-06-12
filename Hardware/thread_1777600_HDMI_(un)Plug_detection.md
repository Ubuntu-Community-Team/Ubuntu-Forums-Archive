---
title: "HDMI (un)Plug detection"
date: 2011-06-07
forum: Hardware
---

### Post by ACDias on 2011-06-07
Is it possible to detect when I plug and unplug a HDMI cable in my notebook?
I've tried udev and acpid, but I didn't find the events I should use to detect when a HDMI is connected.

I've made some scripts to change video and audio config when I'm using my TV, but I don't want to create a shortcut. I want to make it automatically.

Thanks for helping.
:)

---

### Post by Toz on 2011-06-07
Here are a couple of links that might be of use:
[http://askubuntu.com/questions/7292/is-there-a-way-to-autodetect-when-a-display-is-disconnected](http://askubuntu.com/questions/7292/is-there-a-way-to-autodetect-when-a-display-is-disconnected)
[http://ubuntuforums.org/showthread.php?t=1537164](http://ubuntuforums.org/showthread.php?t=1537164)

---

### Post by ACDias on 2011-06-08
I've already saw that... They do with hotkeys... I wanted to do it automatically, but I think no one did it yet.
I'm doing an script to monitor the devices, using disper, but I'm afraid that it would use too much CPU.

I'll test and post here if it works :)

---

### Post by FrAggLE-Rock on 2011-07-09
do you made any progress?

I'm interested in this too

---

### Post by ACDias on 2011-07-11
I didn't finish it yet because I don't have much time to work on it, but here are what I have now:
Everything here I've tested only on my Vaio VPCCW13FX. :P
This script changes the audio output between the notebook and hdmi.
```
#!/bin/bash

declare -i sinks=(`pacmd list-sinks | sed -n -e 's/\**[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'`)
declare -i sinks_count=${#sinks[*]}
declare -i active_sink_index=`pacmd list-sinks | sed -n -e 's/\*[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'`
declare -i next_sink_index=${sinks[0]}

#find the next sink (not always the next index number)
declare -i ord=0
while [ $ord -lt $sinks_count ];
do
    echo ${sinks[$ord]}
    if [ ${sinks[$ord]} -gt $active_sink_index ] ; then
        next_sink_index=${sinks[$ord]}
        break
    fi
    let ord++
done

#change the default sink
pacmd "set-default-sink ${next_sink_index}"

#move all inputs to the new sink
for app in $(pacmd list-sink-inputs | sed -n -e 's/index:[[:space:]]\([[:digit:]]\)/\1/p');
do
    pacmd "move-sink-input $app $next_sink_index"
done
```

This one checks in an infinite loop when I have my LG tv connected through hdmi and calls auto-disper and the script above:
```
#!/bin/sh

DISPER=/usr/bin/disper
is_connected=false
while true
do
  result=`$DISPER -l | grep LG`
  len=$(echo ${#result})
  if [ $len -gt 1 ]
  then
    if eval ! $is_connected
    then
      echo here
      is_connected=true
      sh ./auto-disper --load dock
      bash ./audio-switch.sh
    fi
  else
    if eval $is_connected
    then
      is_connected=false
      sh ./auto-disper --load undock
      bash ./audio-switch.sh
    fi
  fi
  sleep 1
done
```

I have to fix the auto-disper script because it had some wrong variables (I really don't remember exactly what I've changed xD), but here are the version I have:
```
#!/bin/sh
#
# Automatically select a display configuration based on connected devives
#
# Stefan Tomanek <stefan.tomanek@wertarbyte.de>
#
# How to use:
#
# Save your current display configuration and setup with:
#  $ autorandr --save mobile
#
# Connect an additional display, configure your setup and save it:
#  $ autorandr --save docked
#
# Now autorandr can detect which hardware setup is active:
#  $ autorandr
#    mobile
#    docked (detected)
#
# To automatically reload your setup, just append --change to the command line
#
# To manually load a profile, you can use the --load <profile> option.
#
# autorandr tries to avoid reloading an identical configuration. To force the
# (re)configuration, apply --force.
#
# To prevent a profile from being loaded, place a script call "block" in its
# directory. The script is evaluated before the screen setup is inspected, and
# in case of it returning a value of 0 the profile is skipped. This can be used
# to query the status of a docking station you are about to leave.
#
# If no suitable profile can be identified, the current configuration is kept.
# To change this behaviour and switch to a fallback configuration, specify
# --default <profile>
#
# Another script called "postswitch "can be placed in the directory
# ~/.autorandr as well as in all profile directories: The scripts are executed
# after a mode switch has taken place and can notify window managers or other
# applications about it.
#
#
# While the script uses xrandr by defult, calling it by the name "autodisper"
# or "auto-disper" forces it to use the "disper" utility, which is useful for
# controlling nvidia chipsets. The formats for fingerprinting the current setup
# and saving/loading the current configuration are adjusted accordingly.

XRANDR=/usr/bin/xrandr
DISPER=/usr/bin/disper
PROFILES=~/.autorandr
CONFIG=~/.autorandr.conf

CHANGE_PROFILE=0
FORCE_LOAD=0
DEFAULT_PROFILE=""
SAVE_PROFILE=""

FP_METHODS="setup_fp_xrandr_edid setup_fp_sysfs_edid"
CURRENT_CFG_METHOD="current_cfg_xrandr"
LOAD_METHOD="load_cfg_xrandr"

SCRIPTNAME="$(basename $0)"
# when called as autodisper/auto-disper, we assume different defaults
if [ "$SCRIPTNAME" = "auto-disper" ] || [ "$SCRIPTNAME" = "autodisper" ]; then
	FP_METHODS="setup_fp_disper"
	CURRENT_CFG_METHOD="current_cfg_disper"
	LOAD_METHOD="load_cfg_disper"
fi

test -f $CONFIG && . $CONFIG 

setup_fp_xrandr_edid() {
	$XRANDR -q --verbose | awk '
	/^[^ ]+ (dis)?connected / { DEV=$1; }
	$1 ~ /^[a-f0-9]+$/ { ID[DEV] = ID[DEV] $1 }
	END { for (X in ID) { print X " " ID[X]; } }'
}

setup_fp_sysfs_edid() {
	# xrandr triggers the reloading of EDID data
	$XRANDR -q > /dev/null
	# hash the EDIDs of all _connected_ devices
	for P in /sys/class/drm/card*-*/; do
		if grep -q "^connected$" < "${P}status"; then
			echo -n "$(basename "$P") "
			md5sum ${P}edid | awk '{print $1}'
		fi
	done
}

setup_fp_disper() {
	$DISPER -l | grep '^display '
}

setup_fp() {
	local FP="";
	for M in $FP_METHODS; do
		FP="$($M)"
		[ -n "$FP" ] && break;
	done
	if [ -z "$FP" ]; then
		echo "Unable to fingerprint display configuration" >&2
		return
	fi
	echo "$FP"
}

current_cfg_xrandr() {
	$XRANDR -q | awk '
	/^[^ ]+ disconnected / {
        print "output "$1;
	        print "off";
	}
	/^[^ ]+ connected / {
		split($3, A, "+");
		print "output "$1;
		print "mode "A[1];
		print "pos "A[2]"x"A[3];
	}'
}

current_cfg_disper() {
	$DISPER -p
}

current_cfg() {
	$CURRENT_CFG_METHOD;
}

blocked() {
	local PROFILE="$1"
	[ ! -x "$PROFILES/$PROFILE/block" ] && return 1

	"$PROFILES/$PROFILE/block" "$PROFILE"
}

config_equal() {
	local PROFILE="$1"
	if [ "$(cat "$PROFILES/$PROFILE/config")" = "$(current_cfg)" ]; then
		echo "Config already loaded"
		return 0
	else
		return 1
	fi
}

load_cfg_xrandr() {
	sed 's!^!--!' "$1" | xargs $XRANDR
}

load_cfg_disper() {
	$DISPER -i < "$1"
}

load() {
	local PROFILE="$1"
	local CONF="$PROFILES/$PROFILE/config"
	if [ -e "$CONF" ] ; then
		echo " -> loading profile $PROFILE"
echo $CONF
		$LOAD_METHOD "$CONF"

		[ -x "$PROFILES/$PROFILE/postswitch" ] && \
			"$PROFILES/$PROFILE/postswitch" "$PROFILE"
		[ -x "$PROFILES/postswitch" ] && \
			"$PROFILES/postswitch" "$PROFILE"
	fi
}

help() {
	cat <<EOH
Usage: $SCRIPTNAME [options]

-h, --help 		get this small help
-c, --change 		reload current setup
-s, --save <profile>	save your current setup to profile <profile>
-l, --load <profile> 	load profile <profile>
-d, --default <profile> make profile <profile> the default profile 
--force			force (re)loading of a profile
--fingerprint		fingerprint your current hardware setup

 To prevent a profile from being loaded, place a script call "block" in its
 directory. The script is evaluated before the screen setup is inspected, and
 in case of it returning a value of 0 the profile is skipped. This can be used
 to query the status of a docking station you are about to leave.

 If no suitable profile can be identified, the current configuration is kept.
 To change this behaviour and switch to a fallback configuration, specify
 --default <profile>.

 Another script called "postswitch "can be placed in the directory
 ~/.autorandr as well as in any profile directories: The scripts are executed
 after a mode switch has taken place and can notify window managers.

 When called by the name "autodisper" or "auto-disper", the script uses "disper"
 instead of "xrandr" to detect, configure and save the display configuration.

EOH
	exit
}
# process parameters
OPTS=$(getopt -n autorandr -o s:l:d:cfh --long change,default:,save:,load:,force,fingerprint,help -- "$@")
if [ $? != 0 ] ; then echo "Terminating..." >&2 ; exit 1 ; fi
eval set -- "$OPTS"

while true; do
	case "$1" in
		-c|--change) CHANGE_PROFILE=1; shift ;;
		-d|--default) DEFAULT_PROFILE="$2"; shift 2 ;;
		-s|--save) SAVE_PROFILE="$2"; shift 2 ;;
		-l|--load) LOAD_PROFILE="$2"; shift 2 ;;
	 	-h|--help) help ;; 
		--force) FORCE_LOAD=1; shift ;;
		--fingerprint) setup_fp; exit 0;;
		--) shift; break ;;
		*) echo "Error: $1"; exit 1;;
	esac
done

CURRENT_SETUP="$(setup_fp)"

if [ -n "$SAVE_PROFILE" ]; then
	echo "Saving current configuration as profile '${SAVE_PROFILE}'"
	mkdir -p "$PROFILES/$SAVE_PROFILE"
	echo "$CURRENT_SETUP" > "$PROFILES/$SAVE_PROFILE/setup"
	current_cfg > "$PROFILES/$SAVE_PROFILE/config"
	exit 0
fi

if [ -n "$LOAD_PROFILE" ]; then
	CHANGE_PROFILE=1 FORCE_LOAD=1 load "$LOAD_PROFILE"
	exit $?
fi

for SETUP_FILE in $PROFILES/*/setup; do
	if ! [ -e $SETUP_FILE ]; then
		break
	fi
	PROFILE="$(basename $(dirname "$SETUP_FILE"))"
	echo -n "$PROFILE"

	if blocked "$PROFILE"; then
		echo " (blocked)"
		continue
	fi

	FILE_SETUP="$(cat "$PROFILES/$PROFILE/setup")"
	if [ "$CURRENT_SETUP" = "$FILE_SETUP" ]; then
		echo " (detected)"
		if [ "$CHANGE_PROFILE" -eq 1 ]; then
			if [ "$FORCE_LOAD" -eq 1 ] || ! config_equal "$PROFILE"; then
				load "$PROFILE"
			fi
		fi
		# found the profile, exit with success
		exit 0
	else
		echo ""
	fi
done

# we did not find the profile, load default
if [ -n "$DEFAULT_PROFILE" ]; then
	echo "No suitable profile detected, falling back to $DEFAULT_PROFILE"
	load "$DEFAULT_PROFILE"
fi
exit 1
```

You have to download disper and create the profiles for hdmi unplugged and plugged with auto-disper. :)

If you want to help... Sometimes it just does not work and I don't know why. Sometimes it works like a charm :)

---

