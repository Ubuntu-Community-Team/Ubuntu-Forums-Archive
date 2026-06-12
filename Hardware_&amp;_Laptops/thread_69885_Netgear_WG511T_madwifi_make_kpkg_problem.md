---
title: "Netgear WG511T madwifi make kpkg problem"
date: 2005-09-28
forum: Hardware &amp; Laptops
---

### Post by dickohead on 2005-09-28
After following this guide: [http://www.marlow.dk/site.php/tech/madwifi](http://www.marlow.dk/site.php/tech/madwifi)

I am now up to the section to do this: 

> 
 After you have installed the packages, change directory to /usr/src and type:

  tar -xzvf madwifi.tar.gz
  cd kernel-source-x.y.z
  fakeroot make-kpkg --append-to-version "-flavour" --revision 2.x.y-z --added-modules madwifi modules_image


And i am getting returned with this massively worrying error:

```

 I note you are using a hyphen in the revision number.
 Please ensure that the upstream and debian revision
 numbers are policy compliant enough that dpkg and
 shall not choke on them at the end of the compile
for module in /usr/src/modules/madwifi ; do                       \
          if test -d  $module; then                                \
    (cd $module;                                          \
              if ./debian/rules KVERS="2.6.10-amd64" KSRC="/usr/src/linux-source-2.6.10" \
                             KMAINT="Unknown Kernel Package Maintainer" KEMAIL="unknown@unconfigured.in.etc.kernel-pkg.conf"      \
                             KPKG_DEST_DIR="/usr/src/linux-source-2.6.10/.."       \
                             KPKG_MAINTAINER="Unknown Kernel Package Maintainer"        \
                             KPKG_EXTRAV_ARG="EXTRAVERSION=-amd64"        \
                             ARCH="x86_64"                  \
                             KDREV="2.6.10-5" kdist_image; then    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \
                      echo "in fact being built as root, please file a bug ";  \
                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
         read ans;                                        \
              fi;                                                   \
     );                                                    \
  fi;                                                      \
        done
make[1]: Entering directory `/usr/src/modules/madwifi'
/usr/bin/make -C /usr/src/modules/madwifi  KERNELPATH=/usr/src/linux-source-2.6.10 KERNELRELEASE=2.6.10-amd64 TARGET=x86_64-elf
make[2]: Entering directory `/usr/src/modules/madwifi'
Checking if all requirements are met... ok.
mkdir -p ./symbols
for i in ./ath_hal ath_rate/sample ./net80211 ./ath; do \
        /usr/bin/make -C $i || exit 1; \
done
make[3]: Entering directory `/usr/src/modules/madwifi/ath_hal'
/usr/bin/make -C /usr/src/linux-source-2.6.10 SUBDIRS=/usr/src/modules/madwifi/ath_hal MODVERDIR=/usr/src/modules/madwifi/ath_hal/../symbols modules
make[4]: Entering directory `/usr/src/linux-source-2.6.10'
  CC [M]  /usr/src/modules/madwifi/ath_hal/ah_osdep.o
/bin/sh: /pub/gnu/bin/x86_64-linux-gcc: No such file or directory
make[5]: *** [/usr/src/modules/madwifi/ath_hal/ah_osdep.o] Error 1
make[4]: *** [_module_/usr/src/modules/madwifi/ath_hal] Error 2
make[4]: Leaving directory `/usr/src/linux-source-2.6.10'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/usr/src/modules/madwifi/ath_hal'
make[2]: *** [all] Error 1
make[2]: Leaving directory `/usr/src/modules/madwifi'
make[1]: *** [module] Error 2
make[1]: Leaving directory `/usr/src/modules/madwifi'
Module /usr/src/modules/madwifi failed.
Hit return to Continue

```

And that's about it...... If anyone knows how i can fix this it would be much appreciated, i just went and bought a brand new netgear WG511T wireless card due to the fact i read it worked, now i find that i can't install it. Really fed up right now.

:o(

---

