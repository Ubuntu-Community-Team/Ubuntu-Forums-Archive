---
title: "Samsung drivers changing rights"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by poupoul2 on 2007-07-14
Hi all.

Just to inform you about [a recent post on the french Ubuntu]("http://forum.ubuntu-fr.org/viewtopic.php?id=133574") forum about Samsung drivers (sorry, in french). It appears that Samsung unified drivers change rights on some parts of the system: After installing the drivers, applications may launch using root rights, without asking any password. 

What is more, you may be able to kill your system, by deleting system components, generally modifiable only by using sudo. 

The dangerous drivers are [here]("http://www.samsung.com/uk/support/productsupport/download/FileView.aspx?cttfileid=828690&type=Print+Solutions&typecode=&subtype=Multi+Function+Products&subtypecode=&cmssubtypecode=&model=SCX-4200&filetype=DR&language=&LSSI=/uk/module/ssi/left/lmenu_printsolutions_multifunctionproducts.sec&RSSI=/uk/module/ssi/right/rmenu_printsolutions.sec")

I am not a Samsung device user, but i assume some of you are. Sorry if the news have already spread here

EDIT: The hack part of the drivers
```
wrap_setuid_third_party_application xsane
        wrap_setuid_third_party_application xscanimage

        wrap_setuid_ooo_application soffice
        wrap_setuid_ooo_application swriter
        wrap_setuid_ooo_application simpress
        wrap_setuid_ooo_application scalc
```
and
```
wrap_setuid_third_party_application() {
        if echo "$1" | grep -q "/" ; then
                APP_NAME=$1
        else
                APP_NAME=`which $1 2> /dev/null`
        fi
        NEW_NAME=${APP_NAME}.bin

        if test -n "$APP_NAME" ; then
                if ! test -f "$NEW_NAME" && ! test -d "$NEW_NAME"; then
                        mv "$APP_NAME" "$NEW_NAME"
                        cp -af /opt/${VENDOR}/mfp/bin/suwrap "$APP_NAME"
                        chown root:root "$APP_NAME"
                        chmod 4755 "$APP_NAME"
                fi
        fi
}

wrap_setuid_ooo_application() {
        WRAPPING_BIN=`ls /usr/lib*/*/program/$1.bin /opt/*/program/$1.bin 2> /de
v/null | head -1`
        if test -n "$WRAPPING_BIN" ; then
                ${2}wrap_setuid_third_party_application $WRAPPING_BIN
        fi
}
```

Those sections should be commented out

And give to /etc root privileges```
sudo chown root -R /etc
```

---

### Post by hyg53 on 2007-07-14
I really would like to know the name of the guy responsible for this hack...

---

### Post by poupoul2 on 2007-07-14
I just sent a email to Samsung to inform them about this problem and ask for an urgent fix

---

### Post by shyster. on 2007-07-17
This is great "/. So now that I've installed this POS driver, how do I reverse the changes that it's made? I've made /etc/ belong to root as it should, but I have no idea what to do to fix the other applications. If anyone has a solution that would be great.

EDIT: I've also now uninstalled the unified driver, but it doesn't seem to help.

EDIT 2: Actually I looked over the code in the uninstall script and it seems to unwrap the applications- whatever that means. As follows:

> 	check_related_packages
	if [ "$TOTAL_RELATED_PACKAGES_INSTALLED" = "1" ]; then
		# The last from the group of related packages. Remove common files.
		unwrap_setuid_third_party_application xsane
		unwrap_setuid_third_party_application xscanimage

		wrap_setuid_ooo_application soffice  un
		wrap_setuid_ooo_application swriter  un
		wrap_setuid_ooo_application simpress un
		wrap_setuid_ooo_application scalc    un

		uninstall_common_files

However, I'm not sure if this completely reverses the changes made in the first place.

---

### Post by tweedledee on 2007-07-18
This is hardly news.  My guide to installing the driver from 7 months ago makes note of this ([http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)).  Simply reading the code for the installer is also highly misleading: the installer does not (at least in most cases) actually set anything other than xsane (not openoffice or xscanimage - the latter isn't even on my system, though).  Perhaps they intend to, or it is left over from something older, but this is overblown.

Don't get me wrong - I still think this is a problem that needs to be fixed.  It's just not as bad as being claimed, especially over on slashdot, where there are many comments by people who have no idea what they are talking about.

As for WHY: the Samsung multifunction printers apparently require some sort of root access for scanning, hence xsane being set to run as root.  They should fix their driver to avoid this, but that's what causing it.  If you are just installing a printer, you can follow my guide and undo this change with no harm.

I'm not clear on why /etc (and /usr, /etc/sane.d/, /usr/lib/, /usr/lib/sane/, and various others) are being set to the user instead of root; I'm modifying my original install scrip to reset all of this as well, but the files within those directories are all still root, so from a security standpoint this isn't actually that big a deal.

---

### Post by mwarfield on 2007-07-18
Excuse me?

"but the files within those directories are all still root, so from a security standpoint this isn't actually that big a deal."...

User...

cd /etc
mv shadow shadow-
cp ~/my-shadow shadow
chmod 400 shadow
su
mv shadow- shadow

Or maybe modify your group membership to include wheel or bin or disk or kmem and go after other files/devices with that group in common.  etc etc etc...

QED

A user that owns the directory may rename or remove files in that directory and then may create their own (unless the directory permissions are "sticky", like /tmp).  Yes, this is a very big deal security wise.

The original complainent was also noting that their OpenOffice files were owned by root, so, yes, OpenOffice was running as root.  IOW, the security integrity of entire machine is locally compromised.  How is that overblown?

Samsung has acknowledged the problem and is reportedly working on a fix.

How is it that this was known 7 months ago and was NOT reported as a serious security hole?

---

### Post by Silver Surfer on 2007-07-18
I was wondering why xsane was suddenly giving me the "You try to run XSane as ROOT, that really is DANGEROUS" window when trying to scan things.  Now I know why.  Didn't use to do that until I installed my CLP-510 printer.  Wonder why a company like Samsung would do something that irresponsible.

---

### Post by tweedledee on 2007-07-19
> **mwarfield said:**
> Excuse me?

"but the files within those directories are all still root, so from a security standpoint this isn't actually that big a deal."...

User...

cd /etc
mv shadow shadow-
cp ~/my-shadow shadow
chmod 400 shadow
su
mv shadow- shadow

Or maybe modify your group membership to include wheel or bin or disk or kmem and go after other files/devices with that group in common.  etc etc etc...

QED

A user that owns the directory may rename or remove files in that directory and then may create their own (unless the directory permissions are "sticky", like /tmp).  Yes, this is a very big deal security wise.

This actually illustrates a universal problem with Linux permissions: directory permissions override file permissions (i.e., if I own the directory, I can delete files that I do not own within that directory).  Certainly Samsung exposes this problem, but it's more fundamental than that.  SELinux addresses this problem somewhat, but isn't running in Ubuntu by default.

> The original complainent was also noting that their OpenOffice files were owned by root, so, yes, OpenOffice was running as root.  IOW, the security integrity of entire machine is locally compromised.  How is that overblown?

There must be some locale issues, then - perhaps OO is set to as root in French, but not in my system, or various others I've checked.

> Samsung has acknowledged the problem and is reportedly working on a fix.

How is it that this was known 7 months ago and was NOT reported as a serious security hole?

Actually, this WAS reported, multiple times.  Samsung doesn't care, despite anything they publicly post.  (Do you really think the developers didn't know what they were doing?)  And the response I got from the Linux community boiled down to "it's closed source, just don't use it," even though the major problem is that one SUID command can have extensive repurcussions, which is really a problem with Linux permissions design (to which the typical response is "don't use SUID").

---

### Post by margaf77 on 2007-07-19
So how do I uninstall the Samsung driver?

---

### Post by shyster. on 2007-07-19
> **margaf77 said:**
> So how do I uninstall the Samsung driver?

There's an uninstall script in the tar that you can execute- run it just as you did using the install script and you should be good to go!

---

### Post by margaf77 on 2007-07-20
> **shyster. said:**
> There's an uninstall script in the tar that you can execute- run it just as you did using the install script and you should be good to go!

Thanks, sorry to ask such a stupid question but  had deleted the files and didnt see it.

---

### Post by shyster. on 2007-07-20
> **margaf77 said:**
> Thanks, sorry to ask such a stupid question but  had deleted the files and didnt see it.

No problems- you can just download the tar again and use the included file "uninstall.sh", or alternatively you can find the uninstall file at this location "/opt/Samsung/mfp/uninstall.sh" <-- this should be the default. Hope this helps!

---

### Post by bambou51 on 2007-07-29
I have another problem with this printer. Since the install everytime I start the printer cups-add open itself and I have to re-select the printer or cancel. Any idea on how to avoid this screen ?
But the bigger problem is that my usb external Hard drive mounted at startup crashed after I start my printer. I need to reboot my computer with the printer powered off in order to re-mount my hard drive !
When my hard drive crashed it doesn't appear anymore in /dev where previously ot was /dev/sda5 !
Any idea what the problem can be and how to solve it ?

I tried to use [http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian](http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian) tutorial but I was unable to apply the Fix for the MFP port issue section which seems to be my problem

---

### Post by tweedledee on 2007-07-30
> **bambou51 said:**
> I have another problem with this printer. Since the install everytime I start the printer cups-add open itself and I have to re-select the printer or cancel. Any idea on how to avoid this screen ?
But the bigger problem is that my usb external Hard drive mounted at startup crashed after I start my printer. I need to reboot my computer with the printer powered off in order to re-mount my hard drive !
When my hard drive crashed it doesn't appear anymore in /dev where previously ot was /dev/sda5 !
Any idea what the problem can be and how to solve it ?

I tried to use [http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian](http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian) tutorial but I was unable to apply the Fix for the MFP port issue section which seems to be my problem

I'd suggest posting your question on this thread, where someone has reported getting this printer to work and may be able to help you: [http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621).  You should also provide some indication of Ubuntu version, driver version, and how you did the install.

---

### Post by fernandez.garza on 2007-12-24
That's really interesting and thank you guys for the info. I work at Samsung and i will bring that issue down asap. Keep on informing for a better future :)

---

### Post by tayroni on 2008-04-22
Samsung SCX-4200 scanner does not work on Ubuntu 8.04 Hardy Heron
Summary: I have installed the samsung unified driver in gutsy and on hardy. The scanner works on gutsy but NOT on HARDY.

Description: I've installed the driver first using the script provided by samsung, and manually. The manual installation was done because that the script allows /etc read and write by users (I really want to know the name of the programmer who did this mess!)

In both ways: installation by script or manually, the driver for the printer and scanner works on a clean install of gutsy. The same don't happen for hardy: the printer works but the scanner is not recognized by xsane.

Output of sane-find-scanner (both Gutsy and Hardy). Using sudo scanimage -L, the scanner is found on gutsy, but not on hardy.
__________________________________________________ __________________________________________________ __________________________________________________ _
found USB scanner (vendor=0x04e8 [Samsung], product=0x341b [SCX-4200 Series]) at libusb:002:003
__________________________________________________ __________________________________________________ __________________________________________________ _


On GUTSY (sudo xsane and sudo scanimage -L WORKS), the relevant lines of /var/log/syslog are
__________________________________________________ __________________________________________________ __________________________________________________ _
Apr 21 19:14:25 galileu rmmod: ERROR: Module ppdev does not exist in /proc/modules
Apr 21 19:14:25 galileu kernel: [ 1263.159257] pnp: Device 00:0b disabled.
Apr 21 19:14:25 galileu kernel: [ 1263.246583] pnp: Device 00:0b activated.
Apr 21 19:14:25 galileu kernel: [ 1263.246596] parport_pc 00:0b: reported by Plug and Play ACPI
Apr 21 19:14:25 galileu kernel: [ 1263.246662] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 21 19:14:25 galileu kernel: [ 1263.352916] lp0: using parport0 (interrupt-driven).
Apr 21 19:14:25 galileu kernel: [ 1263.394944] pnp: Device 00:0b disabled.
Apr 21 19:14:25 galileu rmmod: ERROR: Module ppdev does not exist in /proc/modules
Apr 21 19:14:25 galileu kernel: [ 1263.450626] pnp: Device 00:0b activated.
Apr 21 19:14:25 galileu kernel: [ 1263.450638] parport_pc 00:0b: reported by Plug and Play ACPI
Apr 21 19:14:25 galileu kernel: [ 1263.450702] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 21 19:14:25 galileu kernel: [ 1263.564420] lp0: using parport0 (interrupt-driven).
__________________________________________________ __________________________________________________ __________________________________________________ _


On HARDY (sudo xsane DOESN'T WORK and sudo scanimage -L don't find the scanner) the relevant lines of /var/log/syslog are
__________________________________________________ __________________________________________________ __________________________________________________ _
Apr 21 19:11:46 kepler kernel: [ 1166.177485] lp: driver loaded but no devices found
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.236853] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.253490] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.257871] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.275009] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:11:46 kepler rmmod: ERROR: Module ppdev does not exist in /proc/modules
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.282338] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.287454] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:11:46 kepler kernel: [ 1166.453319] lp: driver loaded but no devices found
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.511863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.516347] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.562628] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.567925] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.589722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.594256] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:17:01 kepler /USR/SBIN/CRON[7696]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)
__________________________________________________ __________________________________________________ __________________________________________________ _


So, please, help me to figure out what's happening with the samsung scx-4200 scanner on hardy. Any help is welcome.


PS: To install the driver manually (best way), only for reference:

1) Download 20070720152943906_UnifiedLinuxDriver.tar.gz from samsung, extract the files, go to new directory cdroot and type these commands
cp Linux/noarch/at_root/etc/sane.d/smfp.conf /etc/sane.d/
cp -r Linux/noarch/at_opt/share/ppd/* /usr/share/ppd/custom/
cp Linux/i386/at_root/usr/lib/libmfp.so.1.0.1 /usr/lib/
cp Linux/i386/at_root/usr/lib/sane/libsane-smfp.so.1.0.1 /usr/lib/sane/
cp Linux/i386/at_root/usr/lib/cups/backend/mfp /usr/lib/cups/backend/
cp Linux/i386/at_root/usr/lib/cups/filter/* /usr/lib/cups/filter/
cd /usr/lib
ln -s libmfp.so.1.0.1 libmfp.so.1
ln -s libmfp.so.1.0.1 libmfp.so
cd sane
ln -s libsane-smfp.so.1.0.1 libsane-smfp.so.1
ln -s libsane-smfp.so.1.0.1 libsane-smfp.so

2) Edit /etc/sane.d/dll.conf and add the line "smfp" to the end of file. Add yourself to the groups lp and scanner.

3) Reboot

---

