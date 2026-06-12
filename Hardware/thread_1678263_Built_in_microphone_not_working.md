---
title: "Built in microphone not working"
date: 2011-01-30
forum: Hardware
---

### Post by cblnchat on 2011-01-30
The built in microphone isnt working in Ubuntu Netbook Edition on my emachines netbook.  It worked with the last version of ubuntu netbook, although with some choppieness and clicking.  Now it doesnt work at all, with audacity, or with the sound recorder....no noise at all.  Plz help

Thanks

---

### Post by lidex on 2011-01-30
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by cblnchat on 2011-01-31
Sorry but im still kinda new to Ubuntu.  What was the point of that.  I did it and it worked but nothing happened.

---

### Post by lidex on 2011-01-31
> **cblnchat said:**
> Sorry but im still kinda new to Ubuntu.  What was the point of that.  I did it and it worked but nothing happened.

There should be an output file somewhere with a load of diagnostic info. Did you follow the terminal prompts? Did you upload or save the file locally?

---

### Post by cblnchat on 2011-02-01
> **lidex said:**
> There should be an output file somewhere with a load of diagnostic info. Did you follow the terminal prompts? Did you upload or save the file locally?

Yea i found it.  What should i do with it?  Should i attach it to my next post?

---

### Post by lidex on 2011-02-01
You can just copy and paste into message, but use code tags. Copy the text, click the # in the toolbar and then press Ctrl+V

---

### Post by cblnchat on 2011-02-03
> **lidex said:**
> You can just copy and paste into message, but use code tags. Copy the text, click the # in the toolbar and then press Ctrl+V

Ive never used code tags before so ill try.  Thanks

```

  	 	 	 	pre { font-family: "Liberation Serif"; }p { margin-bottom: 0.08in; }  #!/bin/bash  SCRIPT_VERSION=0.4.60 CHANGELOG="http://www.alsa-project.org/alsa-info.sh.changelog"  ################################################################################# #Copyright (C) 2007 Free Software Foundation.  #This program is free software; you can redistribute it and/or modify #it under the terms of the GNU General Public License as published by #the Free Software Foundation; either version 2 of the License, or #(at your option) any later version.  #This program is distributed in the hope that it will be useful, #but WITHOUT ANY WARRANTY; without even the implied warranty of #MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the #GNU General Public License for more details.  #You should have received a copy of the GNU General Public License #along with this program; if not, write to the Free Software #Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.  ##################################################################################  #The script was written for 2 main reasons: # 1. Remove the need for the devs/helpers to ask several questions before we can easily help the user. # 2. Allow newer/inexperienced ALSA users to give us all the info we need to help them.  #Set the locale (this may or may not be a good idea.. let me know) export LC_ALL=C  #Change the PATH variable, so we can run lspci (needed for some distros) PATH=$PATH:/bin:/sbin:/usr/bin:/usr/sbin BGTITLE="ALSA-Info v $SCRIPT_VERSION" PASTEBINKEY="C9cRIO8m/9y8Cs0nVs0FraRx7U0pHsuc" #Define some simple functions  pbcheck(){ 	[[ $UPLOAD = "no" ]] && return  	if [[ -z $PASTEBIN ]]; then 		[[ $(ping -c1 www.alsa-project.org) ]] || KEEP_FILES="yes" UPLOAD="no" PBERROR="yes" 	else 		[[ $(ping -c1 www.pastebin.ca) ]] || KEEP_FILES="yes" UPLOAD="no" PBERROR="yes" 	fi }  update() { 	SHFILE=`mktemp -t alsa-info.XXXXXXXXXX` || exit 1 	wget -O $SHFILE "http://www.alsa-project.org/alsa-info.sh" >/dev/null 2>&1 	REMOTE_VERSION=`grep SCRIPT_VERSION $SHFILE |head -n1 |sed 's/.*=//'` 	if [ "$REMOTE_VERSION" != "$SCRIPT_VERSION" ]; then 		if [[ -n $DIALOG ]] 		then 			OVERWRITE= 			if [ -w $0 ]; then 				dialog --yesno "Newer version of ALSA-Info has been found\n\nDo you wish to install it?\nNOTICE: The original file $0 will be overwritten!" 0 0 				DIALOG_EXIT_CODE=$? 				if [[ $DIALOG_EXIT_CODE = 0 ]]; then 				  OVERWRITE=yes 				fi 			fi 			if [ -z "$OVERWRITE" ]; then 				dialog --yesno "Newer version of ALSA-Info has been found\n\nDo you wish to download it?" 0 0 				DIALOG_EXIT_CODE=$? 			fi 			if [[ $DIALOG_EXIT_CODE = 0 ]] 			then 				echo "Newer version detected: $REMOTE_VERSION" 				echo "To view the ChangeLog, please visit $CHANGELOG" 				if [ "$OVERWRITE" = "yes" ]; then 					cp $SHFILE $0 					echo "ALSA-Info script has been updated to v $REMOTE_VERSION" 					echo "Please re-run the script" 					rm $SHFILE 2>/dev/null 				else 					echo "ALSA-Info script has been downloaded as $SHFILE." 					echo "Please re-run the script from new location." 				fi 				exit 			else 				rm $SHFILE 2>/dev/null 			fi 		else 			echo "Newer version detected: $REMOTE_VERSION" 			echo "To view the ChangeLog, please visit $CHANGELOG" 			if [ -w $0 ]; then 				echo "The original file $0 will be overwritten!" 				echo -n "If you do not like to proceed, press Ctrl-C now.." ; read inp 				cp $SHFILE $0 				echo "ALSA-Info script has been updated. Please re-run it." 				rm $SHFILE 2>/dev/null 			else 				echo "ALSA-Info script has been downloaded $SHFILE." 				echo "Please, re-run it from new location." 			fi 			exit 		fi 	else 		rm $SHFILE 2>/dev/null 	fi }  cleanup() { 	if [ -n "$TEMPDIR" -a "$KEEP_FILES" != "yes" ]; then 		rm -rf "$TEMPDIR" 2>/dev/null 	fi 	test -n "$KEEP_OUTPUT" || rm -f "$NFILE" }   withaplay() {         echo "!!Aplay/Arecord output" >> $FILE         echo "!!------------" >> $FILE         echo "" >> $FILE        	echo "APLAY" >> $FILE 	echo "" >> $FILE  	aplay -l >> $FILE 2>&1         echo "" >> $FILE        	echo "ARECORD" >> $FILE 	echo "" >> $FILE 	arecord -l >> $FILE 2>&1 	echo "" >> $FILE }  withlsmod() { 	echo "!!All Loaded Modules" >> $FILE 	echo "!!------------------" >> $FILE 	echo "" >> $FILE 	lsmod |awk {'print $1'} >> $FILE 	echo "" >> $FILE 	echo "" >> $FILE }  withamixer() {         echo "!!Amixer output" >> $FILE         echo "!!-------------" >> $FILE         echo "" >> $FILE 	for i in `grep "]: " /proc/asound/cards | awk -F ' ' '{ print $1} '` ; do 	CARD_NAME=`grep "^ *$i " $TEMPDIR/alsacards.tmp|awk {'print $2'}` 	echo "!!-------Mixer controls for card $i $CARD_NAME]" >> $FILE 	echo "" >>$FILE 	amixer -c$i info>> $FILE 2>&1 	amixer -c$i>> $FILE 2>&1         echo "" >> $FILE 	done 	echo "" >> $FILE }  withalsactl() { 	echo "!!Alsactl output" >> $FILE         echo "!!-------------" >> $FILE         echo "" >> $FILE         exe=""         if [ -x /usr/sbin/alsactl ]; then         	exe="/usr/sbin/alsactl"         fi         if [ -x /usr/local/sbin/alsactl ]; then         	exe="/usr/local/sbin/alsactl"         fi         if [ -z "$exe" ]; then         	exe=`whereis alsactl | cut -d ' ' -f 2`         fi 	$exe -f $TEMPDIR/alsactl.tmp store 	echo "--startcollapse--" >> $FILE 	cat $TEMPDIR/alsactl.tmp >> $FILE 	echo "--endcollapse--" >> $FILE 	echo "" >> $FILE 	echo "" >> $FILE }  withdevices() {         echo "!!ALSA Device nodes" >> $FILE         echo "!!-----------------" >> $FILE         echo "" >> $FILE         ls -la /dev/snd/* >> $FILE         echo "" >> $FILE         echo "" >> $FILE }  withconfigs() { if [[ -e $HOME/.asoundrc ]] || [[ -e /etc/asound.conf ]] || [[ -e $HOME/.asoundrc.asoundconf ]] then         echo "!!ALSA configuration files" >> $FILE         echo "!!------------------------" >> $FILE         echo "" >> $FILE          #Check for ~/.asoundrc         if [[ -e $HOME/.asoundrc ]]         then                 echo "!!User specific config file (~/.asoundrc)" >> $FILE                 echo "" >> $FILE                 cat $HOME/.asoundrc >> $FILE                 echo "" >> $FILE                 echo "" >> $FILE         fi 	#Check for .asoundrc.asoundconf (seems to be Ubuntu specific) 	if [[ -e $HOME/.asoundrc.asoundconf ]] 	then 		echo "!!asoundconf-generated config file" >> $FILE 		echo "" >> $FILE 		cat $HOME/.asoundrc.asoundconf >> $FILE 		echo "" >> $FILE 		echo "" >> $FILE 	fi         #Check for /etc/asound.conf         if [[ -e /etc/asound.conf ]]         then                 echo "!!System wide config file (/etc/asound.conf)" >> $FILE                 echo "" >> $FILE                 cat /etc/asound.conf >> $FILE                 echo "" >> $FILE                 echo "" >> $FILE         fi fi }  withsysfs() {     local i f     local printed=""     for i in /sys/class/sound/*; do 	case "$i" in 	    */hwC?D?) 		if [ -f $i/init_pin_configs ]; then 		    if [ -z "$printed" ]; then 			echo "!!Sysfs Files" >> $FILE 			echo "!!-----------" >> $FILE 			echo "" >> $FILE 		    fi 		    for f in init_pin_configs driver_pin_configs user_pin_configs init_verbs; do 			echo "$i/$f:" >> $FILE 			cat $i/$f >> $FILE 			echo >> $FILE 		    done 		    printed=yes 		fi 		;; 	    esac     done     if [ -n "$printed" ]; then 	echo "" >> $FILE     fi }  withdmesg() { 	echo "!!ALSA/HDA dmesg" >> $FILE 	echo "!!------------------" >> $FILE 	echo "" >> $FILE 	dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel' >> $FILE 	echo "" >> $FILE 	echo "" >> $FILE }  withall() { 	withdevices 	withconfigs 	withaplay 	withamixer 	withalsactl 	withlsmod 	withsysfs 	withdmesg }  get_alsa_library_version() { 	ALSA_LIB_VERSION=`grep VERSION_STR /usr/include/alsa/version.h 2>/dev/null|awk {'print $3'}|sed 's/"//g'`  	if [ -z "$ALSA_LIB_VERSION" ]; then 		if [ -f /etc/lsb-release ]; then 			. /etc/lsb-release 			case "$DISTRIB_ID" in 				Ubuntu) 					if which dpkg > /dev/null ; then 						ALSA_LIB_VERSION=`dpkg -l libasound2 | tail -1 | awk '{print $3}' | cut -f 1 -d -` 					fi  					if [ "$ALSA_LIB_VERSION" = "<none>" ]; then 						ALSA_LIB_VERSION="" 					fi 					return 					;; 				*) 					return 					;; 			esac 		elif [ -f /etc/debian_version ]; then 			if which dpkg > /dev/null ; then 				ALSA_LIB_VERSION=`dpkg -l libasound2 | tail -1 | awk '{print $3}' | cut -f 1 -d -` 			fi  			if [ "$ALSA_LIB_VERSION" = "<none>" ]; then 				ALSA_LIB_VERSION="" 			fi 			return 		fi 	fi }   #Run checks to make sure the programs we need are installed. LSPCI=$(which lspci 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null); TPUT=$(which tput 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null); DIALOG=$(which dialog 2>/dev/null | sed 's|^[^/]*||' 2>/dev/null);  #Check to see if sysfs is enabled in the kernel. We'll need this later on SYSFS=$(mount |grep sysfs|awk {'print $3'});  #Check modprobe config files for sound related options SNDOPTIONS=$(modprobe -c|sed -n 's/^options \(snd[-_][^ ]*\)/\1:/p')  KEEP_OUTPUT= NFILE=""  PASTEBIN="" WWWSERVICE="www.alsa-project.org" WELCOME="yes" PROCEED="yes" UPLOAD="ask" REPEAT="" while [ -z "$REPEAT" ]; do REPEAT="no" case "$1" in 	--update|--help|--about) 		WELCOME="no" 		PROCEED="no" 		;; 	--upload) 		UPLOAD="yes" 		WELCOME="no" 		;; 	--no-upload) 		UPLOAD="no" 		WELCOME="no" 		;; 	--pastebin) 		PASTEBIN="yes" 		WWWSERVICE="pastebin" 		;; 	--no-dialog) 		DIALOG="" 		REPEAT="" 		shift 		;; 	--stdout) 		DIALOG="" 		UPLOAD="no" 		WELCOME="no" 		TOSTDOUT="yes" 		;; esac done   #Script header output. if [ "$WELCOME" = "yes" ]; then greeting_message="\  This script visits the following commands/files to collect diagnostic information about your ALSA installation and sound related hardware.    dmesg   lspci   lsmod   aplay   amixer   alsactl   /proc/asound/   /sys/class/sound/   ~/.asoundrc (etc.)  See '$0 --help' for command line options. " if [[ -n "$DIALOG" ]]; then 	dialog  --backtitle "$BGTITLE" \ 		--title "ALSA-Info script v $SCRIPT_VERSION" \ 		--msgbox "$greeting_message" 20 80 else 	echo "ALSA Information Script v $SCRIPT_VERSION" 	echo "--------------------------------" 	echo "$greeting_message" fi # dialog fi # WELCOME  #Set the output file TEMPDIR=`mktemp -t -d alsa-info.XXXXXXXXXX` || exit 1 FILE="$TEMPDIR/alsa-info.txt" if [ -z "$NFILE" ]; then 	NFILE=`mktemp -t alsa-info.txt.XXXXXXXXXX` || exit 1 fi  trap cleanup 0  if [ "$PROCEED" = "yes" ]; then  if [[ -z "$LSPCI" ]]  then 	echo "This script requires lspci. Please install it, and re-run this script." 	exit 0 fi  #Fetch the info and store in temp files/variables DISTRO=`grep -ihs "buntu\|SUSE\|Fedora\|PCLinuxOS\|MEPIS\|Mandriva\|Debian\|Damn\|Sabayon\|Slackware\|KNOPPIX\|Gentoo\|Zenwalk\|Mint\|Kubuntu\|FreeBSD\|Puppy\|Freespire\|Vector\|Dreamlinux\|CentOS\|Arch\|Xandros\|Elive\|SLAX\|Red\|BSD\|KANOTIX\|Nexenta\|Foresight\|GeeXboX\|Frugalware\|64\|SystemRescue\|Novell\|Solaris\|BackTrack\|KateOS\|Pardus" /etc/{issue,*release,*version}` KERNEL_VERSION=`uname -r` KERNEL_PROCESSOR=`uname -p` KERNEL_MACHINE=`uname -m` KERNEL_OS=`uname -o` [[ `uname -v |grep SMP`  ]] && KERNEL_SMP="Yes" || KERNEL_SMP="No"  ALSA_DRIVER_VERSION=`cat /proc/asound/version |head -n1|awk {'print $7'} |sed 's/\.$//'` get_alsa_library_version ALSA_UTILS_VERSION=`amixer -v |awk {'print $3'}` VENDOR_ID=`lspci -vn |grep 040[1-3] | awk -F':' '{print $3}'|awk {'print substr($0, 2);}' >$TEMPDIR/vendor_id.tmp` DEVICE_ID=`lspci -vn |grep 040[1-3] | awk -F':' '{print $4}'|awk {'print $1'} >$TEMPDIR/device_id.tmp` LAST_CARD=$((`grep "]: " /proc/asound/cards | wc -l` - 1 ))  ESDINST=$(which esd 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null) PAINST=$(which pulseaudio 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null) ARTSINST=$(which artsd 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null) JACKINST=$(which jackd 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null) DMIDECODE=$(which dmidecode 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)  #Check for DMI data if [ -d /sys/class/dmi/id ]; then     # No root privileges are required when using sysfs method     DMI_SYSTEM_MANUFACTURER=$(cat /sys/class/dmi/id/sys_vendor 2>/dev/null)     DMI_SYSTEM_PRODUCT_NAME=$(cat /sys/class/dmi/id/product_name 2>/dev/null)     DMI_SYSTEM_PRODUCT_VERSION=$(cat /sys/class/dmi/id/product_version 2>/dev/null) elif [ -x $DMIDECODE ]; then     DMI_SYSTEM_MANUFACTURER=$($DMIDECODE -s system-manufacturer 2>/dev/null)     DMI_SYSTEM_PRODUCT_NAME=$($DMIDECODE -s system-product-name 2>/dev/null)     DMI_SYSTEM_PRODUCT_VERSION=$($DMIDECODE -s system-version 2>/dev/null) fi  cat /proc/asound/modules 2>/dev/null|awk {'print $2'}>$TEMPDIR/alsamodules.tmp cat /proc/asound/cards >$TEMPDIR/alsacards.tmp lspci |grep -i "multi\|audio">$TEMPDIR/lspci.tmp  #Check for HDA-Intel cards codec#* cat /proc/asound/card*/codec\#* > $TEMPDIR/alsa-hda-intel.tmp 2> /dev/null  #Check for AC97 cards codec cat /proc/asound/card*/codec97\#0/ac97\#0-0 > $TEMPDIR/alsa-ac97.tmp 2> /dev/null cat /proc/asound/card*/codec97\#0/ac97\#0-0+regs > $TEMPDIR/alsa-ac97-regs.tmp 2> /dev/null  #Check for USB mixer setup cat /proc/asound/card*/usbmixer > $TEMPDIR/alsa-usbmixer.tmp 2> /dev/null  #Fetch the info, and put it in $FILE in a nice readable format. if [[ -z $PASTEBIN ]]; then echo "upload=true&script=true&cardinfo=" > $FILE else echo "name=$USER&type=33&description=/tmp/alsa-info.txt&expiry=&s=Submit+Post&content=" > $FILE fi echo "!!################################" >> $FILE echo "!!ALSA Information Script v $SCRIPT_VERSION" >> $FILE echo "!!################################" >> $FILE echo "" >> $FILE echo "!!Script ran on: `LANG=C TZ=UTC date`" >> $FILE echo "" >> $FILE echo "" >> $FILE echo "!!Linux Distribution" >> $FILE echo "!!------------------" >> $FILE echo "" >> $FILE echo $DISTRO >> $FILE echo "" >> $FILE echo "" >> $FILE echo "!!DMI Information" >> $FILE echo "!!---------------" >> $FILE echo "" >> $FILE echo "Manufacturer:      $DMI_SYSTEM_MANUFACTURER" >> $FILE echo "Product Name:      $DMI_SYSTEM_PRODUCT_NAME" >> $FILE echo "Product Version:   $DMI_SYSTEM_PRODUCT_VERSION" >> $FILE echo "" >> $FILE echo "" >> $FILE echo "!!Kernel Information" >> $FILE echo "!!------------------" >> $FILE echo "" >> $FILE echo "Kernel release:    $KERNEL_VERSION" >> $FILE echo "Operating System:  $KERNEL_OS" >> $FILE echo "Architecture:      $KERNEL_MACHINE" >> $FILE echo "Processor:         $KERNEL_PROCESSOR" >> $FILE echo "SMP Enabled:       $KERNEL_SMP" >> $FILE echo "" >> $FILE echo "" >> $FILE echo "!!ALSA Version" >> $FILE echo "!!------------" >> $FILE echo "" >> $FILE echo "Driver version:     $ALSA_DRIVER_VERSION" >> $FILE echo "Library version:    $ALSA_LIB_VERSION" >> $FILE echo "Utilities version:  $ALSA_UTILS_VERSION" >> $FILE echo "" >> $FILE echo "" >> $FILE echo "!!Loaded ALSA modules" >> $FILE echo "!!-------------------" >> $FILE echo "" >> $FILE cat $TEMPDIR/alsamodules.tmp >> $FILE echo "" >> $FILE echo "" >> $FILE echo "!!Sound Servers on this system" >> $FILE echo "!!----------------------------" >> $FILE echo "" >> $FILE if [[ -n $PAINST ]];then [[ `pgrep '^(.*/)?pulseaudio$'` ]] && PARUNNING="Yes" || PARUNNING="No" echo "Pulseaudio:" >> $FILE echo "      Installed - Yes ($PAINST)" >> $FILE echo "      Running - $PARUNNING" >> $FILE echo "" >> $FILE fi if [[ -n $ESDINST ]];then [[ `pgrep '^(.*/)?esd$'` ]] && ESDRUNNING="Yes" || ESDRUNNING="No" echo "ESound Daemon:" >> $FILE echo "      Installed - Yes ($ESDINST)" >> $FILE echo "      Running - $ESDRUNNING" >> $FILE echo "" >> $FILE fi if [[ -n $ARTSINST ]];then [[ `pgrep '^(.*/)?artsd$'` ]] && ARTSRUNNING="Yes" || ARTSRUNNING="No" echo "aRts:" >> $FILE echo "      Installed - Yes ($ARTSINST)" >> $FILE echo "      Running - $ARTSRUNNING" >> $FILE echo "" >> $FILE fi if [[ -n $JACKINST ]];then [[ `pgrep '^(.*/)?jackd$'` ]] && JACKRUNNING="Yes" || JACKRUNNING="No" echo "Jack:" >> $FILE echo "      Installed - Yes ($JACKINST)" >> $FILE echo "      Running - $JACKRUNNING" >> $FILE echo "" >> $FILE fi if [[ -z "$PAINST" && -z "$ESDINST" && -z "$ARTSINST" && -z "$JACKINST" ]];then echo "No sound servers found." >> $FILE echo "" >> $FILE fi echo "" >> $FILE echo "!!Soundcards recognised by ALSA" >> $FILE echo "!!-----------------------------" >> $FILE echo "" >> $FILE cat $TEMPDIR/alsacards.tmp >> $FILE echo "" >> $FILE echo "" >> $FILE echo "!!PCI Soundcards installed in the system" >> $FILE echo "!!--------------------------------------" >> $FILE echo "" >> $FILE cat $TEMPDIR/lspci.tmp >> $FILE echo "" >> $FILE echo "" >> $FILE echo "!!Advanced information - PCI Vendor/Device/Subsystem ID's" >> $FILE echo "!!--------------------------------------------------------" >> $FILE echo "" >> $FILE lspci -vvn |grep -A1 040[1-3] >> $FILE echo "" >> $FILE echo "" >> $FILE  if [ "$SNDOPTIONS" ] then echo "!!Modprobe options (Sound related)" >> $FILE echo "!!--------------------------------" >> $FILE echo "" >> $FILE modprobe -c|sed -n 's/^options \(snd[-_][^ ]*\)/\1:/p' >> $FILE echo "" >> $FILE echo "" >> $FILE fi  if [ -d "$SYSFS" ] then echo "!!Loaded sound module options" >> $FILE echo "!!--------------------------" >> $FILE echo "" >> $FILE for mod in `cat /proc/asound/modules|awk {'print $2'}`;do echo "!!Module: $mod" >> $FILE for params in `echo $SYSFS/module/$mod/parameters/*`; do 	echo -ne "\t"; 	echo "$params : `cat $params`" | sed 's:.*/::'; done >> $FILE echo "" >> $FILE done echo "" >> $FILE fi  if [ -s "$TEMPDIR/alsa-hda-intel.tmp" ]  then 	echo "!!HDA-Intel Codec information" >> $FILE 	echo "!!---------------------------" >> $FILE 	echo "--startcollapse--" >> $FILE 	echo "" >> $FILE 	cat $TEMPDIR/alsa-hda-intel.tmp >> $FILE 	echo "--endcollapse--" >> $FILE 	echo "" >> $FILE 	echo "" >> $FILE fi  if [ -s "$TEMPDIR/alsa-ac97.tmp" ] then         echo "!!AC97 Codec information" >> $FILE         echo "!!---------------------------" >> $FILE         echo "--startcollapse--" >> $FILE         echo "" >> $FILE         cat $TEMPDIR/alsa-ac97.tmp >> $FILE         echo "" >> $FILE         cat $TEMPDIR/alsa-ac97-regs.tmp >> $FILE         echo "--endcollapse--" >> $FILE 	echo "" >> $FILE 	echo "" >> $FILE fi  if [ -s "$TEMPDIR/alsa-usbmixer.tmp" ] then         echo "!!USB Mixer information" >> $FILE         echo "!!---------------------------" >> $FILE         echo "--startcollapse--" >> $FILE         echo "" >> $FILE         cat $TEMPDIR/alsa-usbmixer.tmp >> $FILE         echo "--endcollapse--" >> $FILE 	echo "" >> $FILE 	echo "" >> $FILE fi  #If no command line options are specified, then run as though --with-all was specified if [[ -z "$1" ]] then 	update 	withall 	pbcheck	 fi  fi # proceed  #loop through command line arguments, until none are left. if [[ -n "$1" ]] then 	until [ -z "$1" ] 	do 	case "$1" in 		--pastebin) 		        update 			withall         		pbcheck 			;; 		--update) 			update 			exit 			;; 		--upload) 			UPLOAD="yes" 			withall 			;; 		--no-upload) 			UPLOAD="no" 			withall 			;; 		--output) 			shift 			NFILE="$1" 			KEEP_OUTPUT="yes" 			;; 		--debug) 			echo "Debugging enabled. $FILE and $TEMPDIR will not be deleted" 			KEEP_FILES="yes" 			echo "" 			withall 			;; 		--with-all) 			withall 			;; 		--with-aplay) 			withaplay 			;; 		--with-amixer) 			withamixer 			;; 		--with-alsactl) 			withalsactl 			;; 		--with-devices) 			withdevices 			;; 		--with-dmesg) 			withdmesg 			;; 		--with-configs) 			if [[ -e $HOME/.asoundrc ]] || [[ -e /etc/asound.conf ]] 			then 				echo "!!ALSA configuration files" >> $FILE 				echo "!!------------------------" >> $FILE 				echo "" >> $FILE  				#Check for ~/.asoundrc 				if [[ -e $HOME/.asoundrc ]] 				then 					echo "!!User specific config file ($HOME/.asoundrc)" >> $FILE 					echo "" >> $FILE 					cat $HOME/.asoundrc >> $FILE 					echo "" >> $FILE 					echo "" >> $FILE 				fi  				#Check for /etc/asound.conf 				if [[ -e /etc/asound.conf ]] 				then 					echo "!!System wide config file (/etc/asound.conf)" >> $FILE 					echo "" >> $FILE 					cat /etc/asound.conf >> $FILE 					echo "" >> $FILE 					echo "" >> $FILE 				fi 			fi 			;; 		--stdout) 			UPLOAD="no" 			withall 			cat $FILE 			rm $FILE 			;; 		--about) 			echo "Written/Tested by the following users of #alsa on irc.freenode.net:" 			echo "" 			echo "	wishie - Script author and developer / Testing" 			echo "	crimsun - Various script ideas / Testing" 			echo "	gnubien - Various script ideas / Testing" 			echo "	GrueMaster - HDA Intel specific items / Testing" 			echo "	olegfink - Script update function" 			echo "  TheMuso - display to stdout functionality" 			exit 0 			;; 		*) 			echo "alsa-info.sh version $SCRIPT_VERSION" 			echo "" 			echo "Available options:" 			echo "	--with-aplay (includes the output of aplay -l)" 			echo "	--with-amixer (includes the output of amixer)" 			echo "	--with-alsactl (includes the output of alsactl)" 			echo "	--with-configs (includes the output of ~/.asoundrc and" 			echo "	    /etc/asound.conf if they exist)"  			echo "	--with-devices (shows the device nodes in /dev/snd/)" 			echo "	--with-dmesg (shows the ALSA/HDA kernel messages)" 			echo "" 			echo "	--output FILE (specify the file to output for no-upload mode)" 			echo "	--update (check server for script updates)" 			echo "	--upload (upload contents to remote server)" 			echo "	--no-upload (do not upload contents to remote server)" 			echo "	--pastebin (use http://pastebin.ca) as remote server" 			echo "	    instead www.alsa-project.org" 			echo "	--stdout (print alsa information to standard output" 			echo "	    instead of a file)" 			echo "	--about (show some information about the script)" 			echo "	--debug (will run the script as normal, but will not" 			echo "	     delete $FILE)" 			exit 0 			;; 	esac 	shift 1 	done fi  if [ "$PROCEED" = "no" ]; then 	exit 1 fi  if [ "$UPLOAD" = "ask" ]; then 	if [[ -n "$DIALOG" ]]; then 		dialog --backtitle "$BGTITLE" --title "Information collected" --yes-label " UPLOAD / SHARE " --no-label " SAVE LOCALLY " --defaultno --yesno "\n\nAutomatically upload ALSA information to $WWWSERVICE?" 10 80 		DIALOG_EXIT_CODE=$? 		if [ $DIALOG_EXIT_CODE != 0 ]; then 			UPLOAD="no" 		else 			UPLOAD="yes" 		fi 	else 		echo -n "Automatically upload ALSA information to $WWWSERVICE? [y/N] : " 		read -e CONFIRM 		if [ "$CONFIRM" != "y" ]; then 			UPLOAD="no" 		else 			UPLOAD="yes" 		fi 	fi  fi  if [ "$UPLOAD" = "no" ]; then  	if [ -z "$TOSTDOUT" ]; then 		mv -f $FILE $NFILE || exit 1 		KEEP_OUTPUT="yes" 	fi  	if [[ -n $DIALOG ]] 	then 		if [[ -n $PBERROR ]]; then 			dialog --backtitle "$BGTITLE" --title "Information collected" --msgbox "An error occurred while contacting the $WWWSERVICE.\n Your information was NOT automatically uploaded.\n\nYour ALSA information is in $NFILE" 10 100 		else 			dialog --backtitle "$BGTITLE" --title "Information collected" --msgbox "\n\nYour ALSA information is in $NFILE" 10 60 		fi 	else 		echo  		if [[ -n $PBERROR ]]; then 			echo "An error occurred while contacting the $WWWSERVICE." 			echo "Your information was NOT automatically uploaded." 			echo "" 			echo "Your ALSA information is in $NFILE" 			echo "" 		else 			if [ -z "$TOSTDOUT" ]; then 				echo "" 				echo "Your ALSA information is in $NFILE" 				echo "" 			fi 		fi 	fi  	exit  fi # UPLOAD  #Test that wget is installed, and supports --post-file. Upload $FILE if it does, and prompt user to upload file if it doesnt.  if WGET=$(which wget 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null); [[ -n "${WGET}" ]] && [[ -x "${WGET}" ]] && [[ `wget --help |grep post-file` ]] then  if [[ -n $DIALOG ]] then  if [[ -z $PASTEBIN ]]; then 	wget -O - --tries=5 --timeout=60 --post-file=$FILE "http://www.alsa-project.org/cardinfo-db/" &>$TEMPDIR/wget.tmp || echo "Upload failed; exit" 	{ for i in 10 20 30 40 50 60 70 80 90; do 		echo $i 		sleep 0.2 	done 	echo; } |dialog --backtitle "$BGTITLE" --guage "Uploading information to www.alsa-project.org ..." 6 70 0 else 	wget -O - --tries=5 --timeout=60 --post-file=$FILE "http://pastebin.ca/quiet-paste.php?api=$PASTEBINKEY&encrypt=t&encryptpw=blahblah" &>$TEMPDIR/wget.tmp || echo "Upload failed; exit" 	{ for i in 10 20 30 40 50 60 70 80 90; do 		echo $i 		sleep 0.2 	done 	echo; } |dialog --backtitle "$BGTITLE" --guage "Uploading information to www.pastebin.ca ..." 6 70 0 fi  dialog --backtitle "$BGTITLE" --title "Information uploaded" --yesno "Would you like to see the uploaded information?" 5 100  DIALOG_EXIT_CODE=$? if [ $DIALOG_EXIT_CODE = 0 ]; then 	grep -v "alsa-info.txt" $FILE >$TEMPDIR/uploaded.txt 	dialog --backtitle "$BGTITLE" --textbox $TEMPDIR/uploaded.txt 0 0 fi  clear  # no dialog else  if [[ -z $PASTEBIN ]]; then 	echo -n "Uploading information to www.alsa-project.org ... "  	wget -O - --tries=5 --timeout=60 --post-file=$FILE http://www.alsa-project.org/cardinfo-db/ &>$TEMPDIR/wget.tmp & else 	echo -n "Uploading information to www.pastebin.ca ... "  	wget -O - --tries=5 --timeout=60 --post-file=$FILE http://pastebin.ca/quiet-paste.php?api=$PASTEBINKEY &>$TEMPDIR/wget.tmp & fi  #Progess spinner for wget transfer. i=1 sp="/-\|" echo -n ' ' while pgrep wget &>/dev/null do 	echo -en "\b${sp:i++%${#sp}:1}" done  echo -e "\b Done!" echo ""  fi #dialog  #See if tput is available, and use it if it is.	 if [[ -n "$TPUT" ]] then 	if [[ -z $PASTEBIN ]]; then 		FINAL_URL=`tput setaf 1; grep "SUCCESS:" $TEMPDIR/wget.tmp | cut -d ' ' -f 2 ; tput sgr0` 	else 		FINAL_URL=`tput setaf 1; grep "SUCCESS:" $TEMPDIR/wget.tmp |sed -n 's/.*\:\([0-9]\+\).*/http:\/\/pastebin.ca\/\1/p';tput sgr0` 	fi else 	if [[ -z $PASTEBIN ]]; then 		FINAL_URL=`grep "SUCCESS:" $TEMPDIR/wget.tmp | cut -d ' ' -f 2` 	else 		FINAL_URL=`grep "SUCCESS:" $TEMPDIR/wget.tmp |sed -n 's/.*\:\([0-9]\+\).*/http:\/\/pastebin.ca\/\1/p'` 	fi fi  #Output the URL of the uploaded file.	 echo "Your ALSA information is located at $FINAL_URL" echo "Please inform the person helping you." echo ""  #We couldnt find a suitable wget, so tell the user to upload manually. else 	mv -f $FILE $NFILE || exit 1 	KEEP_OUTPUT="yes" 	if [[ -z $DIALOG ]] 	then 		if [[ -z $PASTEBIN ]]; then 		echo "" 		echo "Could not automatically upload output to http://www.alsa-project.org" 		echo "Possible reasons are:" 		echo "    1. Couldnt find 'wget' in your PATH" 		echo "    2. Your version of wget is less than 1.8.2" 		echo "" 		echo "Please manually upload $NFILE to http://www.alsa-project.org/cardinfo-db/ and submit your post." 		echo "" 		else 		echo "" 		echo "Could not automatically upload output to http://www.pastebin.ca" 		echo "Possible reasons are:" 		echo "    1. Couldnt find 'wget' in your PATH" 		echo "    2. Your version of wget is less than 1.8.2" 		echo "" 		echo "Please manually upload $NFILE to http://www.pastebin.ca/upload.php and submit your post." 		echo "" 		fi 	else 		if [[ -z $PASTEBIN ]]; then 			dialog --backtitle "$BGTITLE" --msgbox "Could not automatically upload output to http://www.alsa-project.org.\nPossible reasons are:\n\n    1. Couldn't find 'wget' in your PATH\n    2. Your version of wget is less than 1.8.2\n\nPlease manually upload $NFILE to http://www.alsa-project,org/cardinfo-db/ and submit your post." 25 100 		else 			dialog --backtitle "$BGTITLE" --msgbox "Could not automatically upload output to http://www.pastebin.ca.\nPossible reasons are:\n\n    1. Couldn't find 'wget' in your PATH\n    2. Your version of wget is less than 1.8.2\n\nPlease manually upload $NFILE to http://www.pastebin.ca/upload.php and submit your post." 25 100 		fi 	fi fi  
```

---

### Post by lidex on 2011-02-09
Sorry for the delay. That is the actual script, not the output. Can you try again?

---

### Post by cblnchat on 2011-02-09
> **lidex said:**
> Sorry for the delay. That is the actual script, not the output. Can you try again?

Its cool.  And yea sorry i didnt know where to find the output the first time.

```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Wed Feb  9 22:07:18 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      eMachines 
Product Name:      eM250           
Product Version:   V1.25


!!Kernel Information
!!------------------

Kernel release:    2.6.35-25-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x58340000 irq 46


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
    Subsystem: 1025:022f


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
    bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_msi : -1
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    power_save : 0
    power_save_controller : Y
    probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC272X
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0272
Subsystem Id: 0x1025022f
Revision Id: 0x100001
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC272X Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x35 0x35]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x35 0x35]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x8b 0x8b]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC272X Analog", type="Audio", device=0
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=4, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 8
     0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00] [0x00]
  Connection: 2
     0x02 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400700: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x99a30930: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x0c* 0x0d
Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003c: IN OUT HP EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x0c* 0x0d
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000034: IN OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40050c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00]
  Pincap 0x00000010: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00001734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x03a19820: [Jack] Mic at Ext Left
    Conn = 1/8, Color = Pink
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=08, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 3
     0x0c* 0x0d 0x0e
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00001734: IN OUT Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000173c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 3
     0x0c* 0x0d 0x0e
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4016892d: [N/A] Speaker at Ext N/A
    Conn = Digital, Color = Purple
    DefAssociation = 0x2, Sequence = 0xd
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400780: Mono Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
Node 0x21 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0321401f: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 3
     0x0c 0x0d* 0x0e
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x00 0x00]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1d 0x14 0x15 0x16 0x0b 0x13
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 7 Feb  9 13:52 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 6 Feb  9 13:52 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 5 Feb  9 13:52 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 4 Feb  9 13:52 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 3 Feb  9 13:52 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Feb  9 13:52 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Feb  9 13:52 .
drwxr-xr-x 3 root root 180 Feb  9 13:52 ..
lrwxrwxrwx 1 root root  12 Feb  9 13:52 pci-0000:00:1b.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0x58340000 irq 46'
  Mixer name    : 'Realtek ALC272X'
  Components    : 'HDA:10ec0272,1025022f,00100001'
  Controls      : 14
  Simple ctrls  : 8
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 53 [83%] [-11.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 252 [99%] [0.60dB]
  Front Right: Playback 252 [99%] [0.60dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [off]
  Front Right: Playback 23 [74%] [0.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [off]
  Front Right: Capture 0 [0%] [-16.50dB] [off]


!!Alsactl output
!!-------------

--startcollapse--
state.Intel {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 64'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Speaker Playback Volume'
        value.0 64
        value.1 64
    }
    control.2 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Speaker Playback Switch'
        value.0 true
        value.1 true
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 64'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 64
        value.1 64
    }
    control.4 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Headphone Playback Switch'
        value.0 true
        value.1 true
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Mic Playback Volume'
        value.0 0
        value.1 0
    }
    control.6 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Mic Playback Switch'
        value.0 false
        value.1 false
    }
    control.7 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 3'
        comment.dbmin 0
        comment.dbmax 3000
        iface MIXER
        name 'Mic Boost'
        value.0 0
        value.1 0
    }
    control.8 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Capture Switch'
        value.0 false
        value.1 false
    }
    control.9 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -1650
        comment.dbmax 3000
        iface MIXER
        name 'Capture Volume'
        value.0 0
        value.1 0
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Beep Playback Volume'
        value.0 23
        value.1 23
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Beep Playback Switch'
        value.0 false
        value.1 false
    }
    control.12 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 64'
        comment.dbmin -6400
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value 53
    }
    control.13 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.14 {
        comment.access 'read write user'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 255'
        comment.tlv '0000000100000008ffffec1400000014'
        comment.dbmin -5100
        comment.dbmax 0
        iface MIXER
        name 'PCM Playback Volume'
        value.0 252
        value.1 252
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
parport_pc
ppdev
snd_hda_codec_realtek
joydev
snd_hda_intel
snd_hda_codec
snd_hwdep
i915
snd_pcm
snd_seq_midi
drm_kms_helper
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
lib80211_crypt_tkip
snd_seq_device
drm
uvcvideo
wl
snd
intel_agp
videodev
v4l1_compat
psmouse
serio_raw
led_class
soundcore
lib80211
snd_page_alloc
agpgart
i2c_algo_bit
video
output
lp
parport
ahci
libahci
atl1c


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x11 0x411111f0
0x12 0x99a30930
0x13 0x411111f0
0x14 0x99130110
0x15 0x411111f0
0x16 0x411111f0
0x17 0x411111f0
0x18 0x03a19820
0x19 0x411111f0
0x1a 0x411111f0
0x1b 0x411111f0
0x1d 0x4016892d
0x1e 0x411111f0
0x21 0x0321401f

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   20.875551] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   20.877942] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.878060]   alloc irq_desc for 46 on node -1
[   20.878068]   alloc kstat_irqs on node -1
[   20.878096] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   20.878159] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.041141] Skipping EDID probe due to cached edid
[   21.058741] hda_codec: ALC272X: BIOS auto-probing.
[   21.398022] ppdev: user-space parallel port driver


```

ok hope that works and helps

Thanks

---

### Post by lidex on 2011-02-15
Sorry for the delay. Can you provide some mobo info please.
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by jsmooth on 2011-02-15
hey guys im a noob to ubuntu and have been fighting with my internal mic on my toshiba satellite t135 for about a week. finally got it workin. heres what worked for me.
1)go to terminal and type sudo apt-get install gnome-alsa mixer
2)still in terminal type sudo aptitude --purge reinstall linux-sound-base alsa-utils linux-image-`username -r`
3)Go to applications-sound and video-gnome alsa mixer and click the box for mic f and also the analog mic boost.
This is what finally got my internal mic workin in skype.
ps. also make sure that in the skype-options-sound devices you dont have automatically allow skype to adjust my mixer level box checked.
Hope this helps someone and saves them a week worth of searching the net

---

### Post by cblnchat on 2011-02-15
> **lidex said:**
> Sorry for the delay. Can you provide some mobo info please.
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

```

  	 	 	 	p { margin-bottom: 0.08in; }  SMBIOS 2.4 present.  
 

 Handle 0x0000, DMI type 0, 24 bytes  
 BIOS Information  
 	Vendor: Acer  
 	Version: V1.25  
 	Release Date: 11/28/2009  
 	ROM Size: 1024 kB  
 	Characteristics:  
 		PCI is supported  
 		BIOS is upgradeable  
 		BIOS shadowing is allowed  
 		Boot from CD is supported  
 		Selectable boot is supported  
 		BIOS ROM is socketed  
 		EDD is supported  
 		Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)  
 		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)  
 		5.25"/360 KB floppy services are supported (int 13h)  
 		5.25"/1.2 MB floppy services are supported (int 13h)  
 		3.5"/720 KB floppy services are supported (int 13h)  
 		3.5"/2.88 MB floppy services are supported (int 13h)  
 		8042 keyboard services are supported (int 9h)  
 		CGA/mono video services are supported (int 10h)  
 		ACPI is supported  
 		USB legacy is supported  
 		Targeted content distribution is supported 


```


```

   	 	 	 	p { margin-bottom: 0.08in; }  # dmidecode 2.9
 SMBIOS 2.4 present.
 

 Handle 0x0002, DMI type 2, 16 bytes
 Base Board Information
 	Manufacturer: Acer
 	Product Name: eM250            
 	Version: V1.25
 	Serial Number: Base Board Serial Number
 	Asset Tag: Base Board Asset Tag
 	Features:
 		Board is a hosting board
 		Board is replaceable
 	Location In Chassis: Base Board Chassis Location
 	Chassis Handle: 0x0003
 	Type: Motherboard
 	Contained Object Handles: 0
 

 Handle 0x0006, DMI type 10, 6 bytes
 On Board Device Information
 	Type: Video
 	Status: Enabled
 	Description: Video Graphics Controller

```


Hope this helps.  Thanks

---

### Post by lidex on 2011-02-16
Try adding a model switch to alsa-base.conf
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

If no help, then try a different model name. Replace "auto" with:
```
acer
acer-aspire
acer-dmic
```
Only one at a time please and reboot to initialize.

---

### Post by cblnchat on 2011-02-20
That worked perfectly!  It took a bit of messing with but i now have a mic that works.  Although there is a LOT of white noise and static and clicking.  Is there anything i can do to fix that?

Thanks

---

### Post by lidex on 2011-02-22
You may need to play around with the levels in alsamixer. Too much gain can cause that.

---

### Post by cblnchat on 2011-03-14
> **lidex said:**
> You may need to play around with the levels in alsamixer. Too much gain can cause that.
I still havent figured that out.  But im now having problems with other applications that record sound.  Ive gotten it to work in guvcview, but thats it.  Im having problems with sound it Jokosher and Audacity.  And the built in sound recorder.  Is there anything i can do to fix this?  


Thanks

---

### Post by lidex on 2011-03-18
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by cblnchat on 2011-03-23
Ok i got the script
its in a link so i guess ill just give you that
[http://www.alsa-project.org/db/?f=c252a4f85034953c1def4df57f64a1a4c24da218](http://www.alsa-project.org/db/?f=c252a4f85034953c1def4df57f64a1a4c24da218)

it was mostly gibberish to me but whats the Architecture? i686?

Thanks

---

### Post by cblnchat on 2011-05-09
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

hey are you still watchin this thread...sorry i just havent figured out the problem yet.

thanks

---

### Post by lidex on 2011-05-09
> **cblnchat said:**
> hey are you still watchin this thread...sorry i just havent figured out the problem yet.

thanks

Yep. Did you try the other model options?

---

### Post by cblnchat on 2011-05-25
> **lidex said:**
> Yep. Did you try the other model options?

Hey, sorry ive taken so long to get back.
But it almost seems like my mic has fixed its self.  After i updated to 11.04 i just started working, its taken a little fixing to get it to work well (thanks to your previous instruction) but it seems to be working with everything now.

Thanks for all the help btw!

---

### Post by lidex on 2011-05-25
Great. I think you can mark the thread solved now. Use the 'Thread Tools' option up top.

---

### Post by srisharan on 2011-06-30
thank you guys worked perfectly

---

