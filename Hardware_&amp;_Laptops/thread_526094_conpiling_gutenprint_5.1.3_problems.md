---
title: "conpiling gutenprint 5.1.3 problems"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by dukemaru on 2007-08-15
have an Epson pm A890 printer that I would like to get working on Feisty,
I downloaded the new gutenprint-5.1.3 in hopes that it would hold the solution to my inability to print,
Unfortunately I can't seem to get make install to work.
I did the following:
./configure
make
make install

It went through configure with no errors and seemed to do well with make as well but when I ran make install this is the output I got:

rich@rich-desktop:~/gutenprint-5.1.3$ sudo make install
Making install in include
make[1]: Entering directory `/home/rich/gutenprint-5.1.3/include'
Making install in gutenprint
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/include/gutenprint'
make[3]: Entering directory `/home/rich/gutenprint-5.1.3/include/gutenprint'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/gutenprint" || mkdir -p -- "/usr/local/include/gutenprint"
 /usr/bin/install -c -m 644 'gutenprint-version.h' '/usr/local/include/gutenprint/gutenprint-version.h'
test -z "/usr/local/include/gutenprint" || mkdir -p -- "/usr/local/include/gutenprint"
 /usr/bin/install -c -m 644 'gutenprint.h' '/usr/local/include/gutenprint/gutenprint.h'
 /usr/bin/install -c -m 644 'gutenprint-module.h' '/usr/local/include/gutenprint/gutenprint-module.h'
 /usr/bin/install -c -m 644 'array.h' '/usr/local/include/gutenprint/array.h'
 /usr/bin/install -c -m 644 'bit-ops.h' '/usr/local/include/gutenprint/bit-ops.h'
 /usr/bin/install -c -m 644 'channel.h' '/usr/local/include/gutenprint/channel.h'
 /usr/bin/install -c -m 644 'color.h' '/usr/local/include/gutenprint/color.h'
 /usr/bin/install -c -m 644 'curve-cache.h' '/usr/local/include/gutenprint/curve-cache.h'
 /usr/bin/install -c -m 644 'curve.h' '/usr/local/include/gutenprint/curve.h'
 /usr/bin/install -c -m 644 'dither.h' '/usr/local/include/gutenprint/dither.h'
 /usr/bin/install -c -m 644 'sequence.h' '/usr/local/include/gutenprint/sequence.h'
 /usr/bin/install -c -m 644 'image.h' '/usr/local/include/gutenprint/image.h'
 /usr/bin/install -c -m 644 'list.h' '/usr/local/include/gutenprint/list.h'
 /usr/bin/install -c -m 644 'module.h' '/usr/local/include/gutenprint/module.h'
 /usr/bin/install -c -m 644 'mxml.h' '/usr/local/include/gutenprint/mxml.h'
 /usr/bin/install -c -m 644 'paper.h' '/usr/local/include/gutenprint/paper.h'
 /usr/bin/install -c -m 644 'path.h' '/usr/local/include/gutenprint/path.h'
 /usr/bin/install -c -m 644 'printers.h' '/usr/local/include/gutenprint/printers.h'
 /usr/bin/install -c -m 644 'sequence.h' '/usr/local/include/gutenprint/sequence.h'
 /usr/bin/install -c -m 644 'string-list.h' '/usr/local/include/gutenprint/string-list.h'
 /usr/bin/install -c -m 644 'util.h' '/usr/local/include/gutenprint/util.h'
 /usr/bin/install -c -m 644 'vars.h' '/usr/local/include/gutenprint/vars.h'
 /usr/bin/install -c -m 644 'weave.h' '/usr/local/include/gutenprint/weave.h'
 /usr/bin/install -c -m 644 'xml.h' '/usr/local/include/gutenprint/xml.h'
make[3]: Leaving directory `/home/rich/gutenprint-5.1.3/include/gutenprint'
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/include/gutenprint'
Making install in gutenprintui2
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/include/gutenprintui2'
make[3]: Entering directory `/home/rich/gutenprint-5.1.3/include/gutenprintui2'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/gutenprintui2" || mkdir -p -- "/usr/local/include/gutenprintui2"
make[3]: Leaving directory `/home/rich/gutenprint-5.1.3/include/gutenprintui2'
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/include/gutenprintui2'
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/include'
make[3]: Entering directory `/home/rich/gutenprint-5.1.3/include'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/rich/gutenprint-5.1.3/include'
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/include'
make[1]: Leaving directory `/home/rich/gutenprint-5.1.3/include'
Making install in src
make[1]: Entering directory `/home/rich/gutenprint-5.1.3/src'
Making install in main
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/src/main'
make[3]: Entering directory `/home/rich/gutenprint-5.1.3/src/main'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  'libgutenprint.la' '/usr/local/lib/libgutenprint.la'
/usr/bin/install -c .libs/libgutenprint.so.2.0.0 /usr/local/lib/libgutenprint.so.2.0.0
(cd /usr/local/lib && { ln -s -f libgutenprint.so.2.0.0 libgutenprint.so.2 || { rm -f libgutenprint.so.2 && ln -s libgutenprint.so.2.0.0 libgutenprint.so.2; }; })
(cd /usr/local/lib && { ln -s -f libgutenprint.so.2.0.0 libgutenprint.so || { rm -f libgutenprint.so && ln -s libgutenprint.so.2.0.0 libgutenprint.so; }; })
/usr/bin/install -c .libs/libgutenprint.lai /usr/local/lib/libgutenprint.la
/usr/bin/install -c .libs/libgutenprint.a /usr/local/lib/libgutenprint.a
chmod 644 /usr/local/lib/libgutenprint.a
ranlib /usr/local/lib/libgutenprint.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/lib/pkgconfig" || mkdir -p -- "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'gutenprint.pc' '/usr/local/lib/pkgconfig/gutenprint.pc'
test -z "/usr/local/lib/gutenprint/5.1.3/modules" || mkdir -p -- "/usr/local/lib/gutenprint/5.1.3/modules"
test -z "/usr/local/share/gutenprint/5.1.3/xml" || mkdir -p -- "/usr/local/share/gutenprint/5.1.3/xml"
 /usr/bin/install -c -m 644 'dither-matrix-1x1.xml' '/usr/local/share/gutenprint/5.1.3/xml/dither-matrix-1x1.xml'
 /usr/bin/install -c -m 644 'dither-matrix-2x1.xml' '/usr/local/share/gutenprint/5.1.3/xml/dither-matrix-2x1.xml'
 /usr/bin/install -c -m 644 'dither-matrix-4x1.xml' '/usr/local/share/gutenprint/5.1.3/xml/dither-matrix-4x1.xml'
 /usr/bin/install -c -m 644 'papers.xml' '/usr/local/share/gutenprint/5.1.3/xml/papers.xml'
 /usr/bin/install -c -m 644 'printers.xml' '/usr/local/share/gutenprint/5.1.3/xml/printers.xml'
make[3]: Leaving directory `/home/rich/gutenprint-5.1.3/src/main'
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/src/main'
Making install in gutenprintui2
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/src/gutenprintui2'
make[3]: Entering directory `/home/rich/gutenprint-5.1.3/src/gutenprintui2'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
test -z "/usr/local/lib/pkgconfig" || mkdir -p -- "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'gutenprintui2.pc' '/usr/local/lib/pkgconfig/gutenprintui2.pc'
make[3]: Leaving directory `/home/rich/gutenprint-5.1.3/src/gutenprintui2'
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/src/gutenprintui2'
Making install in escputil
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/src/escputil'
make[3]: Entering directory `/home/rich/gutenprint-5.1.3/src/escputil'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /bin/bash ../../libtool --mode=install /usr/bin/install -c 'escputil' '/usr/local/bin/escputil'
/usr/bin/install -c .libs/escputil /usr/local/bin/escputil
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/rich/gutenprint-5.1.3/src/escputil'
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/src/escputil'
Making install in gimp2
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/src/gimp2'
make[3]: Entering directory `/home/rich/gutenprint-5.1.3/src/gimp2'
make[3]: Nothing to be done for `install-exec-am'.
test -z "" || mkdir -p -- ""
make[3]: Leaving directory `/home/rich/gutenprint-5.1.3/src/gimp2'
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/src/gimp2'
Making install in cups
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/src/cups'
make[3]: Entering directory `/home/rich/gutenprint-5.1.3/src/cups'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
test -z "/usr/lib/cups/driver" || mkdir -p -- "/usr/lib/cups/driver"
test -z "/usr/lib/cups/filter" || mkdir -p -- "/usr/lib/cups/filter"
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
if test -n "" -a -n "" ; then \
          mkdir -p -- /usr/share/cups/model/gutenprint/5.1/; \
          cd ppd ; \
          for language in * ; do \
            cd ..; \
            mkdir -p -- /usr/share/cups/model/gutenprint/5.1//$language; \
            cd ppd/$language; \
            for ppdfile in * ; do \
              (cd ../..; /usr/bin/install -c -m 644 ppd/$language/$ppdfile /usr/share/cups/model/gutenprint/5.1//$language) ; \
            done; \
          cd ..; \
          done \
        fi
test -z "/usr/share/cups" || mkdir -p -- "/usr/share/cups"
test -z "/etc/cups" || mkdir -p -- "/etc/cups"
make  install-data-hook
make[4]: Entering directory `/home/rich/gutenprint-5.1.3/src/cups'
Expect a number of "rmdir: Directory not empty" warnings
These messages are harmless and should be ignored.
rmdir /usr/share/cups/model/gutenprint/5.1/
rmdir: /usr/share/cups/model/gutenprint/5.1/: No such file or directory
make[4]: [install-data-hook] Error 1 (ignored)
rmdir /usr/share/cups
rmdir: /usr/share/cups: Directory not empty
make[4]: [install-data-hook] Error 1 (ignored)
rmdir /usr/lib/cups/driver
rmdir: /usr/lib/cups/driver: Directory not empty
make[4]: [install-data-hook] Error 1 (ignored)
rmdir /usr/lib/cups/filter
rmdir: /usr/lib/cups/filter: Directory not empty
make[4]: [install-data-hook] Error 1 (ignored)
rmdir /usr/bin
rmdir: /usr/bin: Directory not empty
make[4]: [install-data-hook] Error 1 (ignored)
rmdir /usr/lib/cups
rmdir: /usr/lib/cups: Directory not empty
make[4]: [install-data-hook] Error 1 (ignored)
rmdir /etc/cups
rmdir: /etc/cups: Directory not empty
make[4]: [install-data-hook] Error 1 (ignored)
rmdir `dirname /usr/share/cups`
rmdir: /usr/share: Directory not empty
make[4]: [install-data-hook] Error 1 (ignored)
rmdir `dirname /usr/lib/cups`
rmdir: /usr/lib: Directory not empty
make[4]: [install-data-hook] Error 1 (ignored)
rmdir `dirname /etc/cups`
rmdir: /etc: Directory not empty
make[4]: [install-data-hook] Error 1 (ignored)
make[4]: Leaving directory `/home/rich/gutenprint-5.1.3/src/cups'
make[3]: Leaving directory `/home/rich/gutenprint-5.1.3/src/cups'
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/src/cups'
Making install in foomatic
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/src/foomatic'
make[3]: Entering directory `/home/rich/gutenprint-5.1.3/src/foomatic'
make[3]: Nothing to be done for `install-exec-am'.
if test -n "foomatic-data" ; then \
          make install-kit FOOMATIC_DB=foomatic-db/gutenprint-ijs.5.1 ; \
          make install-kit FOOMATIC_DB=foomatic-db/gutenprint-ijs-simplified.5.1 ; \
        fi
make[4]: Entering directory `/home/rich/gutenprint-5.1.3/src/foomatic'
if test -n "" ; then \
          mkdir -p -- `/usr/sbin/foomatic-kitload -l` ; \
          /usr/sbin/foomatic-kitload -f -d  -k foomatic-db/gutenprint-ijs.5.1 ; \
        else \
          /usr/sbin/foomatic-kitload -f -k foomatic-db/gutenprint-ijs.5.1 ; \
        fi
./
./opt/
./opt/gutenprint-ijs.5.1-color.xml
./opt/gutenprint-ijs.5.1-pagesize.xml
./opt/gutenprint-ijs.5.1-stp_adjustdotsize.xml
./opt/gutenprint-ijs.5.1-stp_borderless.xml
./opt/gutenprint-ijs.5.1-stp_cdinnerradius.xml
./opt/gutenprint-ijs.5.1-stp_colorcorrection.xml
./opt/gutenprint-ijs.5.1-stp_ditheralgorithm.xml
./opt/gutenprint-ijs.5.1-stp_duplex.xml
./opt/gutenprint-ijs.5.1-stp_enableblackdensity.xml
./opt/gutenprint-ijs.5.1-stp_enableblackgamma.xml
./opt/gutenprint-ijs.5.1-stp_enableblacktrans.xml
./opt/gutenprint-ijs.5.1-stp_enablebluedensity.xml
./opt/gutenprint-ijs.5.1-stp_enablecyanbalance.xml
./opt/gutenprint-ijs.5.1-stp_enablecyandensity.xml
./opt/gutenprint-ijs.5.1-stp_enablecyangamma.xml
./opt/gutenprint-ijs.5.1-stp_enabledarkgraytransition.xml
./opt/gutenprint-ijs.5.1-stp_enabledarkyellowtransition.xml
./opt/gutenprint-ijs.5.1-stp_enabledensity.xml
./opt/gutenprint-ijs.5.1-stp_enablegcrlower.xml
./opt/gutenprint-ijs.5.1-stp_enablegcrupper.xml
./opt/gutenprint-ijs.5.1-stp_enablegamma.xml
./opt/gutenprint-ijs.5.1-stp_enableglosslimit.xml
./opt/gutenprint-ijs.5.1-stp_enablegray1transition.xml
./opt/gutenprint-ijs.5.1-stp_enablegray2transition.xml
./opt/gutenprint-ijs.5.1-stp_enablegray3transition.xml
./opt/gutenprint-ijs.5.1-stp_enablegraytransition.xml
./opt/gutenprint-ijs.5.1-stp_enableinklimit.xml
./opt/gutenprint-ijs.5.1-stp_enablelightcyantransition.xml
./opt/gutenprint-ijs.5.1-stp_enablelightgraytransition.xml
./opt/gutenprint-ijs.5.1-stp_enablelightmagentatransition.xml
./opt/gutenprint-ijs.5.1-stp_enablelightyellowtransition.xml
./opt/gutenprint-ijs.5.1-stp_enablemagentabalance.xml
./opt/gutenprint-ijs.5.1-stp_enablemagentadensity.xml
./opt/gutenprint-ijs.5.1-stp_enablemagentagamma.xml
./opt/gutenprint-ijs.5.1-stp_enablereddensity.xml
./opt/gutenprint-ijs.5.1-stp_enableyellowbalance.xml
./opt/gutenprint-ijs.5.1-stp_enableyellowdensity.xml
./opt/gutenprint-ijs.5.1-stp_enableyellowgamma.xml
./opt/gutenprint-ijs.5.1-stp_fullbleed.xml
./opt/gutenprint-ijs.5.1-stp_imagetype.xml
./opt/gutenprint-ijs.5.1-stp_inkset.xml
./opt/gutenprint-ijs.5.1-stp_inktype.xml
./opt/gutenprint-ijs.5.1-stp_inputslot.xml
./opt/gutenprint-ijs.5.1-stp_laminate.xml
./opt/gutenprint-ijs.5.1-stp_linearcontrast.xml
./opt/gutenprint-ijs.5.1-stp_mediatype.xml
./opt/gutenprint-ijs.5.1-stp_printingdirection.xml
./opt/gutenprint-ijs.5.1-stp_quality.xml
./opt/gutenprint-ijs.5.1-stp_resolution.xml
./opt/gutenprint-ijs.5.1-stp_usegloss.xml
./opt/gutenprint-ijs.5.1-stp_weave.xml
./opt/gutenprint-ijs.5.1-stp_blackdensity-1.xml
./opt/gutenprint-ijs.5.1-stp_blackgamma-1.xml
./opt/gutenprint-ijs.5.1-stp_blacktrans-1.xml
./opt/gutenprint-ijs.5.1-stp_bluedensity-1.xml
./opt/gutenprint-ijs.5.1-stp_brightness-1.xml
./opt/gutenprint-ijs.5.1-stp_cdxadjustment-1.xml
./opt/gutenprint-ijs.5.1-stp_cdyadjustment-1.xml
./opt/gutenprint-ijs.5.1-stp_contrast-1.xml
./opt/gutenprint-ijs.5.1-stp_cyanbalance-1.xml
./opt/gutenprint-ijs.5.1-stp_cyandensity-1.xml
./opt/gutenprint-ijs.5.1-stp_cyangamma-1.xml
./opt/gutenprint-ijs.5.1-stp_darkgraytransition-1.xml
./opt/gutenprint-ijs.5.1-stp_darkyellowtransition-1.xml
./opt/gutenprint-ijs.5.1-stp_density-1.xml
./opt/gutenprint-ijs.5.1-stp_gcrlower-1.xml
./opt/gutenprint-ijs.5.1-stp_gcrupper-1.xml
./opt/gutenprint-ijs.5.1-stp_gamma-1.xml
./opt/gutenprint-ijs.5.1-stp_glosslimit-1.xml
./opt/gutenprint-ijs.5.1-stp_gray1transition-1.xml
./opt/gutenprint-ijs.5.1-stp_gray2transition-1.xml
./opt/gutenprint-ijs.5.1-stp_gray3transition-1.xml
./opt/gutenprint-ijs.5.1-stp_graytransition-1.xml
./opt/gutenprint-ijs.5.1-stp_inklimit-1.xml
./opt/gutenprint-ijs.5.1-stp_inklimit-2.xml
./opt/gutenprint-ijs.5.1-stp_inklimit-3.xml
./opt/gutenprint-ijs.5.1-stp_inklimit-4.xml
./opt/gutenprint-ijs.5.1-stp_inklimit-5.xml
./opt/gutenprint-ijs.5.1-stp_inklimit-6.xml
./opt/gutenprint-ijs.5.1-stp_lightcyantransition-1.xml
./opt/gutenprint-ijs.5.1-stp_lightgraytransition-1.xml
./opt/gutenprint-ijs.5.1-stp_lightmagentatransition-1.xml
./opt/gutenprint-ijs.5.1-stp_lightyellowtransition-1.xml
./opt/gutenprint-ijs.5.1-stp_magentabalance-1.xml
./opt/gutenprint-ijs.5.1-stp_magentadensity-1.xml
./opt/gutenprint-ijs.5.1-stp_magentagamma-1.xml
./opt/gutenprint-ijs.5.1-stp_reddensity-1.xml
./opt/gutenprint-ijs.5.1-stp_yellowbalance-1.xml
./opt/gutenprint-ijs.5.1-stp_yellowdensity-1.xml
./opt/gutenprint-ijs.5.1-stp_yellowgamma-1.xml
./opt/gutenprint-ijs.5.1-printoutmode.xml
./opt/gutenprint-ijs.5.1-model.xml
./opt/gutenprint-ijs.5.1-resolution.xml
./driver/
./driver/gutenprint-ijs.5.1.xml

Kit successfully installed! The list of written files you find in
/usr/share/foomatic/kitload.log.
make[4]: Leaving directory `/home/rich/gutenprint-5.1.3/src/foomatic'
make[4]: Entering directory `/home/rich/gutenprint-5.1.3/src/foomatic'
if test -n "" ; then \
          mkdir -p -- `/usr/sbin/foomatic-kitload -l` ; \
          /usr/sbin/foomatic-kitload -f -d  -k foomatic-db/gutenprint-ijs-simplified.5.1 ; \
        else \
          /usr/sbin/foomatic-kitload -f -k foomatic-db/gutenprint-ijs-simplified.5.1 ; \
        fi
./
./opt/
./opt/gutenprint-ijs-simplified.5.1-color.xml
./opt/gutenprint-ijs-simplified.5.1-pagesize.xml
./opt/gutenprint-ijs-simplified.5.1-stp_borderless.xml
./opt/gutenprint-ijs-simplified.5.1-stp_cdinnerradius.xml
./opt/gutenprint-ijs-simplified.5.1-stp_duplex.xml
./opt/gutenprint-ijs-simplified.5.1-stp_fullbleed.xml
./opt/gutenprint-ijs-simplified.5.1-stp_imagetype.xml
./opt/gutenprint-ijs-simplified.5.1-stp_inkset.xml
./opt/gutenprint-ijs-simplified.5.1-stp_inktype.xml
./opt/gutenprint-ijs-simplified.5.1-stp_inputslot.xml
./opt/gutenprint-ijs-simplified.5.1-stp_laminate.xml
./opt/gutenprint-ijs-simplified.5.1-stp_mediatype.xml
./opt/gutenprint-ijs-simplified.5.1-stp_quality.xml
./opt/gutenprint-ijs-simplified.5.1-stp_resolution.xml
./opt/gutenprint-ijs-simplified.5.1-stp_usegloss.xml
./opt/gutenprint-ijs-simplified.5.1-stp_brightness-1.xml
./opt/gutenprint-ijs-simplified.5.1-stp_contrast-1.xml
./opt/gutenprint-ijs-simplified.5.1-printoutmode.xml
./opt/gutenprint-ijs-simplified.5.1-model.xml
./opt/gutenprint-ijs-simplified.5.1-resolution.xml
./driver/
./driver/gutenprint-ijs-simplified.5.1.xml

Kit successfully installed! The list of written files you find in
/usr/share/foomatic/kitload.log.
make[4]: Leaving directory `/home/rich/gutenprint-5.1.3/src/foomatic'
make[3]: Leaving directory `/home/rich/gutenprint-5.1.3/src/foomatic'
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/src/foomatic'
Making install in ghost
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/src/ghost'
make[3]: Entering directory `/home/rich/gutenprint-5.1.3/src/ghost'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/rich/gutenprint-5.1.3/src/ghost'
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/src/ghost'
Making install in testpattern
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/src/testpattern'
make[3]: Entering directory `/home/rich/gutenprint-5.1.3/src/testpattern'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /bin/bash ../../libtool --mode=install /usr/bin/install -c 'testpattern' '/usr/local/bin/testpattern'
/usr/bin/install -c .libs/testpattern /usr/local/bin/testpattern
test -z "/usr/local/share/gutenprint/samples" || mkdir -p -- "/usr/local/share/gutenprint/samples"
 /usr/bin/install -c -m 644 'testpattern.sample' '/usr/local/share/gutenprint/samples/testpattern.sample'
 /usr/bin/install -c -m 644 'extended.sample' '/usr/local/share/gutenprint/samples/extended.sample'
make[3]: Leaving directory `/home/rich/gutenprint-5.1.3/src/testpattern'
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/src/testpattern'
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/src'
make[3]: Entering directory `/home/rich/gutenprint-5.1.3/src'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/rich/gutenprint-5.1.3/src'
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/src'
make[1]: Leaving directory `/home/rich/gutenprint-5.1.3/src'
Making install in samples
make[1]: Entering directory `/home/rich/gutenprint-5.1.3/samples'
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/samples'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/gutenprint/samples" || mkdir -p -- "/usr/local/share/gutenprint/samples"
 /usr/bin/install -c -m 644 'colorbars4.png' '/usr/local/share/gutenprint/samples/colorbars4.png'
 /usr/bin/install -c -m 644 'colorsweep.png' '/usr/local/share/gutenprint/samples/colorsweep.png'
 /usr/bin/install -c -m 644 'profile.jpg' '/usr/local/share/gutenprint/samples/profile.jpg'
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/samples'
make[1]: Leaving directory `/home/rich/gutenprint-5.1.3/samples'
Making install in test
make[1]: Entering directory `/home/rich/gutenprint-5.1.3/test'
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/test'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/test'
make[1]: Leaving directory `/home/rich/gutenprint-5.1.3/test'
Making install in po
make[1]: Entering directory `/home/rich/gutenprint-5.1.3/po'
/bin/sh `case "scripts/mkinstalldirs" in /*) echo "scripts/mkinstalldirs" ;; *) echo "../scripts/mkinstalldirs" ;; esac` /usr/local/share
mkdir -p -- /usr/local/share/locale/cs/LC_MESSAGES
installing cs.gmo as /usr/local/share/locale/cs/LC_MESSAGES/gutenprint.mo
mkdir -p -- /usr/local/share/locale/da/LC_MESSAGES
installing da.gmo as /usr/local/share/locale/da/LC_MESSAGES/gutenprint.mo
mkdir -p -- /usr/local/share/locale/de/LC_MESSAGES
installing de.gmo as /usr/local/share/locale/de/LC_MESSAGES/gutenprint.mo
mkdir -p -- /usr/local/share/locale/el/LC_MESSAGES
installing el.gmo as /usr/local/share/locale/el/LC_MESSAGES/gutenprint.mo
mkdir -p -- /usr/local/share/locale/en_GB/LC_MESSAGES
installing en_GB.gmo as /usr/local/share/locale/en_GB/LC_MESSAGES/gutenprint.mo
mkdir -p -- /usr/local/share/locale/es/LC_MESSAGES
installing es.gmo as /usr/local/share/locale/es/LC_MESSAGES/gutenprint.mo
mkdir -p -- /usr/local/share/locale/fr/LC_MESSAGES
installing fr.gmo as /usr/local/share/locale/fr/LC_MESSAGES/gutenprint.mo
mkdir -p -- /usr/local/share/locale/hu/LC_MESSAGES
installing hu.gmo as /usr/local/share/locale/hu/LC_MESSAGES/gutenprint.mo
mkdir -p -- /usr/local/share/locale/ja/LC_MESSAGES
installing ja.gmo as /usr/local/share/locale/ja/LC_MESSAGES/gutenprint.mo
mkdir -p -- /usr/local/share/locale/nb/LC_MESSAGES
installing nb.gmo as /usr/local/share/locale/nb/LC_MESSAGES/gutenprint.mo
mkdir -p -- /usr/local/share/locale/nl/LC_MESSAGES
installing nl.gmo as /usr/local/share/locale/nl/LC_MESSAGES/gutenprint.mo
mkdir -p -- /usr/local/share/locale/pl/LC_MESSAGES
installing pl.gmo as /usr/local/share/locale/pl/LC_MESSAGES/gutenprint.mo
mkdir -p -- /usr/local/share/locale/pt/LC_MESSAGES
installing pt.gmo as /usr/local/share/locale/pt/LC_MESSAGES/gutenprint.mo
mkdir -p -- /usr/local/share/locale/sk/LC_MESSAGES
installing sk.gmo as /usr/local/share/locale/sk/LC_MESSAGES/gutenprint.mo
mkdir -p -- /usr/local/share/locale/sv/LC_MESSAGES
installing sv.gmo as /usr/local/share/locale/sv/LC_MESSAGES/gutenprint.mo
mkdir -p -- /usr/local/share/locale/zh_TW/LC_MESSAGES
installing zh_TW.gmo as /usr/local/share/locale/zh_TW/LC_MESSAGES/gutenprint.mo
if test "gutenprint" = "gettext"; then \
          /bin/sh `case "scripts/mkinstalldirs" in /*) echo "scripts/mkinstalldirs" ;; *) echo "../scripts/mkinstalldirs" ;; esac` /usr/local/share/gettext/po; \
          for file in Makefile.in.in Makevars remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.head[/email]er [email]en@boldquot.head[/email]er insert-header.sin Rules-quot  ; do \
            /usr/bin/install -c -m 644 ./$file \
                            /usr/local/share/gettext/po/$file; \
          done; \
        else \
          : ; \
        fi
make[1]: Leaving directory `/home/rich/gutenprint-5.1.3/po'
Making install in man
make[1]: Entering directory `/home/rich/gutenprint-5.1.3/man'
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/man'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man1" || mkdir -p -- "/usr/local/share/man/man1"
 /usr/bin/install -c -m 644 './escputil.1' '/usr/local/share/man/man1/escputil.1'
test -z "/usr/local/share/man/man8" || mkdir -p -- "/usr/local/share/man/man8"
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/man'
make[1]: Leaving directory `/home/rich/gutenprint-5.1.3/man'
Making install in doc
make[1]: Entering directory `/home/rich/gutenprint-5.1.3/doc'
Making install in developer
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/doc/developer'
make[3]: Entering directory `/home/rich/gutenprint-5.1.3/doc/developer'
make[3]: Nothing to be done for `install-exec-am'.
if test -n 'html' ; then \
          mkdir -p -- /usr/local/share/gutenprint/doc/reference-html ; \
          if test -f gutenprint.pdf ; then \
            /usr/bin/install -c -m 644 gutenprint.pdf /usr/local/share/gutenprint/doc ; \
          elif test -f ./gutenprint.pdf ; then \
            /usr/bin/install -c -m 644 ./gutenprint.pdf /usr/local/share/gutenprint/doc ; \
          fi ; \
          if test -d reference-html ; then \
          HTMLGENDIR="reference-html" ; \
          elif test -d ./reference-html ; then \
            HTMLGENDIR="./reference-html" ; \
          else \
            exit 1 ; \
          fi ; \
          for file in $HTMLGENDIR/*.html $HTMLGENDIR/*.css ; do \
            if test -f $file ; then \
              /usr/bin/install -c -m 644 $file /usr/local/share/gutenprint/doc/reference-html ; \
            fi ; \
          done ; \
        fi
make[3]: Leaving directory `/home/rich/gutenprint-5.1.3/doc/developer'
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/doc/developer'
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/doc'
make[3]: Entering directory `/home/rich/gutenprint-5.1.3/doc'
make[3]: Nothing to be done for `install-exec-am'.
mkdir -p -- /usr/local/share/gutenprint/doc
/usr/bin/install -c -m 644 ./FAQ.html /usr/local/share/gutenprint/doc
/usr/bin/install -c -m 644 ./gutenprint-users-manual.odt /usr/local/share/gutenprint/doc
/usr/bin/install -c -m 644 ./gutenprint-users-manual.pdf /usr/local/share/gutenprint/doc
make[3]: Leaving directory `/home/rich/gutenprint-5.1.3/doc'
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/doc'
make[1]: Leaving directory `/home/rich/gutenprint-5.1.3/doc'
Making install in scripts
make[1]: Entering directory `/home/rich/gutenprint-5.1.3/scripts'
make[2]: Entering directory `/home/rich/gutenprint-5.1.3/scripts'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3/scripts'
make[1]: Leaving directory `/home/rich/gutenprint-5.1.3/scripts'
make[1]: Entering directory `/home/rich/gutenprint-5.1.3'
make[2]: Entering directory `/home/rich/gutenprint-5.1.3'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/rich/gutenprint-5.1.3'
make[1]: Leaving directory `/home/rich/gutenprint-5.1.3'
rich@rich-desktop:~/gutenprint-5.1.3$

---

### Post by dukemaru on 2007-08-19
Wow! Am I the only person to have had this problem?
I'm aching for a solution to this one. Anyone?
My printer driver is not available in the default gutenprint that comes with Feisty Fawn, so this is the only way I can see to get the driver I need.

Does anyone else have any ideas?

---

