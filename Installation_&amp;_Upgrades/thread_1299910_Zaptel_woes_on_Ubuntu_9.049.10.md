---
title: "Zaptel woes on Ubuntu 9.04/9.10"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by sr_guy on 2009-10-24
I've been trying to install zaptel on Ubuntu 9.04/9.10 to no avail. I've tried the patch method in the below thread.

[http://ubuntuforums.org/showthread.php?t=1144894](http://ubuntuforums.org/showthread.php?t=1144894) 

Here is my error output:

```

root@virtubuntu:~# m-a -t build zaptel
Extracting the package tarball, /usr/src/zaptel.tar.bz2, please wait...
dh_testdir
dh_testroot
rm -f *-stamp
# Delete the generated bristuff symlinks:
rm -f -f cwain.[ch] qozap.[ch] zaphfc.[ch] ztgsm.[ch]
# Add here commands to clean up after the build process.
rm -rf modexamples
rm -f tonezones.txt
rm -f version.h
rm -rf debian/fake
# * Makefile does not exist when running svn-buildpackage
#   as the source tree is not there.
# FIXME: This will fail with an ugly warning on the clean of the
# modules build. However only fter the actuual clean.
[ ! -f Makefile ] || /usr/bin/make dist-clean || true
make[1]: Entering directory `/usr/src/modules/zaptel'
make: *** menuselect: No such file or directory.  Stop.
make[1]: [clean] Error 2 (ignored)
make: Entering an unknown directory
make: Leaving an unknown directory
rm -f torisatool
rm -f fxotune fxstest sethdlc-new ztcfg ztdiag ztmonitor ztspeed zttest ztscan
rm -f *.o ztcfg tzdriver sethdlc sethdlc-new
rm -f libtonezone.so libtonezone.a *.lo
/usr/bin/make -C /usr/src/linux-headers-2.6.31-14-generic ARCH=i386 SUBDIRS=/usr/src/modules/zaptel/kernel HOTPLUG_FIR            MWARE=yes KBUILD_OBJ_M="pciradio.o tor2.o torisa.o wcfxo.o wct1xxp.o wctdm.o wcte11xp.o wcusb.o zaptel.o ztd-eth.o ztd            -loc.o ztdummy.o ztdynamic.o zttranscode.o wct4xxp/ wctc4xxp/ xpp/ wctdm24xxp/ wcte12xp/" clean
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CLEAN   /usr/src/modules/zaptel/kernel
  CLEAN   /usr/src/modules/zaptel/kernel/.tmp_versions
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[2]: Entering directory `/usr/src/modules/zaptel/kernel/xpp/utils'
rm -f *.o init_fxo_modes print_modes perlcheck zt_registration.8 xpp_sync.8 lszaptel.8 xpp_blink.8 zapconf.8 zaptel_ha            rdware.8
make: *** ppp: No such file or directory.  Stop.
make[2]: Leaving directory `/usr/src/modules/zaptel/kernel/xpp/utils'
make: Entering an unknown directory
make: Leaving an unknown directory
make[1]: *** [clean] Error 2
make[1]: Leaving directory `/usr/src/modules/zaptel'
#rm -f debian/manpage.links  debian/manpage.refs debian/*.8
dh_clean
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/zaptel'
dh_testdir
dh_testroot
rm -f *-stamp
# Delete the generated bristuff symlinks:
rm -f -f cwain.[ch] qozap.[ch] zaphfc.[ch] ztgsm.[ch]
# Add here commands to clean up after the build process.
rm -rf modexamples
rm -f tonezones.txt
rm -f version.h
rm -rf debian/fake
# * Makefile does not exist when running svn-buildpackage
#   as the source tree is not there.
# FIXME: This will fail with an ugly warning on the clean of the
# modules build. However only fter the actuual clean.
[ ! -f Makefile ] || /usr/bin/make dist-clean || true
make[2]: Entering directory `/usr/src/modules/zaptel'
make: Entering an unknown directory
make: *** menuselect: No such file or directory.  Stop.
make: Leaving an unknown directory
make[2]: [clean] Error 2 (ignored)
rm -f torisatool
rm -f fxotune fxstest sethdlc-new ztcfg ztdiag ztmonitor ztspeed zttest ztscan
rm -f *.o ztcfg tzdriver sethdlc sethdlc-new
rm -f libtonezone.so libtonezone.a *.lo
/usr/bin/make -C /usr/src/linux-headers-2.6.31-14-generic ARCH=i386 SUBDIRS=/usr/src/modules/zaptel/kernel HOTPLUG_FIR            MWARE=yes KBUILD_OBJ_M="pciradio.o tor2.o torisa.o wcfxo.o wct1xxp.o wctdm.o wcte11xp.o wcusb.o zaptel.o ztd-eth.o ztd            -loc.o ztdummy.o ztdynamic.o zttranscode.o wct4xxp/ wctc4xxp/ xpp/ wctdm24xxp/ wcte12xp/" clean
make[3]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[3]: Entering directory `/usr/src/modules/zaptel/kernel/xpp/utils'
rm -f *.o init_fxo_modes print_modes perlcheck zt_registration.8 xpp_sync.8 lszaptel.8 xpp_blink.8 zapconf.8 zaptel_ha            rdware.8
make[3]: Leaving directory `/usr/src/modules/zaptel/kernel/xpp/utils'
make: Entering an unknown directory
make: *** ppp: No such file or directory.  Stop.
make: Leaving an unknown directory
make[2]: *** [clean] Error 2
make[2]: Leaving directory `/usr/src/modules/zaptel'
#rm -f debian/manpage.links  debian/manpage.refs debian/*.8
dh_clean
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.31-14-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.31-14-generic/g ;s/#KVERS#/2.6.31-14-generic/g ; s/_KVERS_/2.6.31-14-generic/g ; s/##KDREV            ##/2.6.31-14.48/g ; s/#KDREV#/2.6.31-14.48/g ; s/_KDREV_/2.6.31-14.48/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
dh_clean -k
cp -a /usr/src/modules/zaptel/debian/generated/* .
./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for GNU make... make
checking for grep... /bin/grep
checking for sh... /bin/bash
checking for ln... /bin/ln
checking for wget... /usr/bin/wget
checking for grep that handles long lines and -e... (cached) /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for initscr in -lcurses... yes
checking curses.h usability... yes
checking curses.h presence... yes
checking for curses.h... yes
checking for initscr in -lncurses... yes
checking for curses.h... (cached) yes
checking for newtBell in -lnewt... no
checking for usb_init in -lusb... no
configure: creating ./config.status
config.status: creating build_tools/menuselect-deps
config.status: creating makeopts
config.status: creating build_tools/make_firmware_object
configure: *** Zaptel build successfully configured ***
make MODULES_EXTRA="ds1x1f opvxa1200 wcopenpci cwain qozap zaphfc ztgsm" SUBDIRS_EXTRA="vzaphfc oslec" modules KERNEL_            SOURCES=/usr/src/linux-headers-2.6.31-14-generic MODVERSIONS=detect KERNEL=linux-2.6.31-14-generic
make[2]: Entering directory `/usr/src/modules/zaptel'
make -C /usr/src/linux-headers-2.6.31-14-generic ARCH=i386 SUBDIRS=/usr/src/modules/zaptel/kernel HOTPLUG_FIRMWARE=yes             KBUILD_OBJ_M="pciradio.o tor2.o torisa.o wcfxo.o wct1xxp.o wctdm.o wcte11xp.o wcusb.o zaptel.o ztd-eth.o ztd-loc.o zt            dummy.o ztdynamic.o zttranscode.o ds1x1f.o opvxa1200.o wcopenpci.o cwain.o qozap.o zaphfc.o ztgsm.o wct4xxp/ wctc4xxp/             xpp/ wctdm24xxp/ wcte12xp/ vzaphfc/ oslec/" modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
gcc -o /usr/src/modules/zaptel/kernel/makefw /usr/src/modules/zaptel/kernel/makefw.c
/usr/src/modules/zaptel/kernel/makefw /usr/src/modules/zaptel/kernel/pciradio.rbt radfw > /usr/src/modules/zaptel/kern            el/radfw.h
Loaded 42096 bytes from file
  CC [M]  /usr/src/modules/zaptel/kernel/pciradio.o
/usr/src/modules/zaptel/kernel/makefw /usr/src/modules/zaptel/kernel/tormenta2.rbt tor2fw > /usr/src/modules/zaptel/ke            rnel/tor2fw.h
Loaded 69900 bytes from file
  CC [M]  /usr/src/modules/zaptel/kernel/tor2.o
  CC [M]  /usr/src/modules/zaptel/kernel/torisa.o
/usr/src/modules/zaptel/kernel/torisa.c: In function âtorisa_shutdownâ:
/usr/src/modules/zaptel/kernel/torisa.c:428: warning: suggest parentheses around operand of â!â or change â&â to â&&â             or â!â to â~â
/usr/src/modules/zaptel/kernel/torisa.c:429: warning: suggest parentheses around operand of â!â or change â&â to â&&â             or â!â to â~â
  CC [M]  /usr/src/modules/zaptel/kernel/wcfxo.o
  CC [M]  /usr/src/modules/zaptel/kernel/wct1xxp.o
  CC [M]  /usr/src/modules/zaptel/kernel/wctdm.o
  CC [M]  /usr/src/modules/zaptel/kernel/wcte11xp.o
  CC [M]  /usr/src/modules/zaptel/kernel/wcusb.o
  CC [M]  /usr/src/modules/zaptel/kernel/zaptel-base.o
/usr/src/modules/zaptel/kernel/zaptel-base.c: In function âzt_ppp_xmitâ:
/usr/src/modules/zaptel/kernel/zaptel-base.c:1751: warning: comparison of distinct pointer types lacks a cast
/usr/src/modules/zaptel/kernel/zaptel-base.c:1814: warning: comparison of distinct pointer types lacks a cast
/usr/src/modules/zaptel/kernel/zaptel-base.c: In function âzt_rbs_sethookâ:
/usr/src/modules/zaptel/kernel/zaptel-base.c:2187: warning: suggest parentheses around operand of â!â or change â&â to             â&&â or â!â to â~â
  LD [M]  /usr/src/modules/zaptel/kernel/zaptel.o
  CC [M]  /usr/src/modules/zaptel/kernel/ztd-eth.o
  CC [M]  /usr/src/modules/zaptel/kernel/ztd-loc.o
  CC [M]  /usr/src/modules/zaptel/kernel/ztdummy.o
/usr/src/modules/zaptel/kernel/ztdummy.c: In function âztdummy_hr_intâ:
/usr/src/modules/zaptel/kernel/ztdummy.c:203: error: âstruct hrtimerâ has no member named âexpiresâ
make[4]: *** [/usr/src/modules/zaptel/kernel/ztdummy.o] Error 1
make[3]: *** [_module_/usr/src/modules/zaptel/kernel] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[2]: *** [modules] Error 2
make[2]: Leaving directory `/usr/src/modules/zaptel'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/zaptel'
make: *** [kdist_build] Error 2
BUILD FAILED!
See /var/cache/modass/zaptel-source.buildlog.2.6.31-14-generic.1256401900 for details.
Build failed. Press Return to continue...

```

Has anyone found a solution for this issue? I'm trying to get a working asterisk/freepbx on the newer distros. If zaptel is not properly working, the freepbx blacklist won't either

---

### Post by manickaselvam on 2010-02-02
I'm also trying the Asterisks to work on my machine. I could able to run the softphones (2 extensions created) successfully. But not able to install ZAPTEL drivers. Did you succeeded yours...?

I'm trying in Ubuntu 9.10.

Advanced thanks for the rply.

Manick

---

### Post by HugoSerrano on 2010-02-02
Did you tried to install Dahdi? Zaptel chaged name do Dadhi

Regards

---

### Post by sr_guy on 2010-02-02
I eventually found a solution:

```

cd /usr/src

svn co http://svn.digium.com/svn/asterisk/branches/1.6.1/ asterisk
svn co http://svn.digium.com/svn/asterisk-addons/branches/1.6.1/ asterisk-addons

----------------------------

cd asterisk
./configure
nano -w Makefile
(change all instances of "ASTVARRUNDIR=<something>" to "ASTVARRUNDIR=/var/run/asterisk". If you know a better way, please point it out)
make
sudo make install

cd asterisk-*
make
make install

-------------------------------

#Asterisk 1.6 config
nano -w /etc/asterisk/sip_general_custom.conf
session-timers=refuse

reboot

#Setup Ports
sudo nano -w /etc/asterisk/rtp.conf

rtpstart=10000
rtpend=10100

---------------------------------

sudo nano -w /etc/init.d/asterisk

Copy the init file from here, save. 

http://www.joeterranova.net/wiki/index.php?title=Asterisk-init


sudo chmod +x /etc/init.d/asterisk
sudo chown -R asterisk:asterisk /var/spool/asterisk/ /var/log/asterisk/
sudo update-rc.d asterisk defaults
sudo /etc/init.d/asterisk start

-----------------------

#Mysql Permissions
mysqladmin -uroot -p create asterisk create asteriskcdrdb
echo "GRANT ALL PRIVILEGES ON asterisk.* TO asterisk@localhost IDENTIFIED BY '<asteriskpassword>';" | mysql -u root -p
echo "GRANT ALL PRIVILEGES ON asteriskcdrdb.* TO asterisk@localhost IDENTIFIED BY '<asteriskpassword>';" | mysql -u root -p
Configure Asterisk Files:
sudo nano -w /etc/apache2/apache2.conf
User asterisk
Group asterisk
sudo nano -w /etc/asterisk/asterisk.conf
astrundir => /var/run/asterisk
sudo nano -w /etc/php5/apache2/php.ini
sudo nano -w /etc/php5/cli/php.ini
post_max_size = 20M
upload_max_filesize = 20M
magic_quotes_gpc = Off
memory_limit = 100M

sudo /etc/init.d/apache2 restart

--------------------------


# Get DAHDI Tools / Complete

cd /usr/src
svn co http://svn.digium.com/svn/dahdi/linux-complete/trunk/ linux-complete

cd linux-complete/linux

make
make install

cd linux-complete/tools
./configure
make
make install


```

---

