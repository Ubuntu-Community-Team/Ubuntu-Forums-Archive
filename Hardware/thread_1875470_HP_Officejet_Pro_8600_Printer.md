---
title: "HP Officejet Pro 8600 Printer"
date: 2011-11-04
forum: Hardware
---

### Post by PJSingh5000 on 2011-11-04
Does anyone have experience with the HP Officejet Pro 8600 Printer?

Here is the printer on HP's web site:
[http://www.shopping.hp.com/product/printer/Officejet+Pro/1/storefronts/CM750A%2523B1H]("http://www.shopping.hp.com/product/printer/Officejet+Pro/1/storefronts/CM750A%2523B1H")

I did find that there is HPLIP Linux support for this printer, but wanted to hear some feedback and personal experiences about this device from forum members.

The documentation listing capabilities supported by Linux is here:
[http://hplipopensource.com/hplip-web/models/officejet/officejet_pro_8600.html]("http://hplipopensource.com/hplip-web/models/officejet/officejet_pro_8600.html")

One specific question I have is, can you access the printer's Media/SD Card reader over your network?

In the Notes section, the above documentation states "USB mass storage only. You may mount the photocard as a storage drive over USB only. Refer to your distribution's documentation for setup and usage instructions." 

I have an older HP 2510 PhotoSmart All-In-One, and I am able to access its multi-readers through my network in Nautilus by using "smb://<PRINTER_IP_ADDRESS>".  I find it hard to believe that HP would abandon this nice feature (is it Samba support??).  If you are using this printer, would you please confirm if you can access the 8600's SD Card reader from Ubuntu?

Also, please share your other experiences?  (reliability, ink cartridge usage, scan speed, print speed, etc.).

---

### Post by PJSingh5000 on 2012-09-14
It's been some time.
Has anyone tried the HP Officejet Pro with Ubuntu?

---

### Post by z_mikowski on 2012-09-26
I just bought this printer for $149(!).  My experience with HP and Linux has always been at least good.  This product is similar to a $349 device the small company I worked for previously (heck, it might even be the same model - I don't recall), and that printed perfectly with my Linux laptop and desktop.  I didn't do much else with it - maybe I scanned once or twice.

I am replacing my OfficeJet 6320(?) printer, which lasted 3 years.  I expect this printer to last about as long.

I will report back after I get some time with it.  It should be delivered tomorrow or Friday.

---

### Post by z_mikowski on 2012-09-29
Initial reports:

Printer works just fine, at least as much as I have needed it to date.  Duplex printing works great.

The scanner works with hplip installed, but one page at a time. All I want is to scan in multi-page documents and convert to pdf.  I tried skanlite, simple-scan, hp's scan interface from hplip (see hp-systray), xsane, and gscan2pdf.

gscan2pdf looks most promising.  But it is stymied by an image corruption problem somewhere upstream.  Also, the auto document feeder does not seem to send an end of document notification so gscan2pdf keeps scanning air for a couple of pages before erroring out.  I expect both these problems to be fixed, but until then, I have a work around ...

Here is a script I have tested to convert a multi-page document into a single pdf.  Save it as /usr/local/bin/scan-base and sudo ln -s /usr/local/bin/scan-base /usr/local/bin/scan-pdf.  Then just type scan-pdf into a terminal whenever you want to create a pdf document.  It will drop the image into your home directory.  You will need to adjust the --device-name parameter to that provided by HPLIP.  The reason why this works and gscan2pdf doesn't is I am using the tiff format for scan images.  The default pbm format appears to be what is used by gscan2pdf, and that cannot be processed by convert.  You need imagemagick and ghostscript installed at least for this script to work.

```

#!/bin/bash

# This stop on first error; unfortunately convert complains
# so we can not use it at present (scanimage output images have errors)
# set -e;

# This complains if we try to use unset variables.
set -u;

INVOKE=`basename "$0"`  # can be scan-copy; scan-pdf; scan-copy-pdf; scan-pnm
USER=`whoami`    # user
PROCESSID=$$    # process id for uniqueness
DATETIME=`date +%Y%m%d_%H%M%S`
TMPDIR="/tmp/scan_${USER}_${DATETIME}_${PROCESSID}"
PDFILE="$HOME/scan_${DATETIME}_${PROCESSID}.pdf"

if [ ! -d "${HOME}" ] || [ ! -x "${HOME}" ] || [ ! -d "${HOME}" ]; then
  echo "${INVOKE}: \$HOME environment variable does not appear to"
  echo "${INVOKE}: be properly set.  Make sure it points to your"
  echo "${INVOKE}: home directory, e.g. type: export HOME='/home/me'."
  echo "${INVOKE}: Exiting."
  exit 0
fi

function MKTMP {
  if [ -a "${TMPDIR}" ]; then
    echo "Temporary directory for scan already exists!"
    echo "  ( ${TMPDIR} )"
    echo "  ABORTING!"
    exit 0
  fi  
  mkdir -p "${TMPDIR}"
  if [ ! -r "${TMPDIR}" ]; then
    echo "Cannot create temporary directory for scan!"
    echo "  ( $TMPDIR )"
    echo "  ABORTING!"
    exit 0
  fi  
}

function SCANIT () {
  echo -n "How many pages? ";
  read count;

  # TODO See scanimage -L to get list of devices.
  # May wish to have user select on start

  /usr/bin/scanimage \
    --device-name='hpaio:/net/Officejet_Pro_8600?ip=192.168.1.2' \
    -l 0 -t 0 -x 215.9 -y 279.4 \
    --source=ADF --batch=scan%02d.tiff --batch-count ${count} \
    --format=tiff --mode=color --resolution=300;
}

function CONVERTIT () {
  convert -density 300x300 -geometry 2550x3300 *.tiff out.ps;
  ps2pdf out.ps out.pdf;
}

function PRINTIT () {
  ls *.pnm |while read -r LINE
  do
    BASE=`basename "${LINE}" ".pnm"`;
    convert "${LINE}" "${BASE}.ps";
    lpr -P hp8600 "${BASE}.ps";
  done
}

function CLEANUP () {
  if [ -r "out.pdf" ]; then
    mv out.pdf "${PDFILE}"
  fi  
  cd "${HOME}"
  rm -rf "${TMPDIR}"
}

case $INVOKE in  
  scan-copy)
    MKTMP; cd "${TMPDIR}"; SCANIT; PRINTIT; CLEANUP
  ;;    
  scan-pdf)
    MKTMP; cd "${TMPDIR}"; SCANIT; CONVERTIT; CLEANUP
  ;;  
  scan-copy-pdf)
    MKTMP; cd "${TMPDIR}"; SCANIT; CONVERTIT; CLEANUP
  ;;  
  scan-img)
    MKTMP; cd "${TMPDIR}"; SCANIT
    cd "${HOME}"; mv "${TMPDIR}" ./ ;;
  *)  
    echo "command $INVOKE not supported by scan-simple"
  ;;  
esac
exit 0

```

---

### Post by PJSingh5000 on 2012-10-12
z_mikowski,

Thanks so much for sharing your experience and the script.

I was also looking forward to multi page scan capabilities using the printer's auto-feeder. So this is a disappoinement.  I wonder if they will update the driver to allow multi-page scan to work??

Regarding merging individual PDFs, I like to use the PDFmod because it has an easy to use GUI.

---

### Post by itcave on 2012-11-26
I thought this printer would scan single and multiple pages direct to a network folder or email in jpg or PDF? If this is true (is it?) Then what's the advantage of using scanning software on Ubuntu?

---

### Post by cartosys on 2013-01-18
This printer worked flawlessly.  I set it up as a wireless network printer.  Opened Printers and Ubuntu discovered it on the network.  Clicked Add and selected the HPLIB driver.  Test page successfully printed.  Opened Simple Scan and was able to scan single or multiple (in simple scan click the drop down next to "Scan" and select "All Pages From Feeder") into a PDF.  Works perfectly!

---

### Post by PJSingh5000 on 2013-06-16
> **cartosys said:**
> This printer worked flawlessly.  I set it up as a wireless network printer.  Opened Printers and Ubuntu discovered it on the network.  Clicked Add and selected the HPLIB driver.  Test page successfully printed.  Opened Simple Scan and was able to scan single or multiple (in simple scan click the drop down next to "Scan" and select "All Pages From Feeder") into a PDF.  Works perfectly!

This is good to hear.  Do you know if the card reader works as well?

---

### Post by TheOnlyChosenOne on 2013-10-20
> **z_mikowski said:**
> Initial reports:

Printer works just fine, at least as much as I have needed it to date.  Duplex printing works great.

The scanner works with hplip installed, but one page at a time. All I want is to scan in multi-page documents and convert to pdf.  I tried skanlite, simple-scan, hp's scan interface from hplip (see hp-systray), xsane, and gscan2pdf.

gscan2pdf looks most promising.  But it is stymied by an image corruption problem somewhere upstream.  Also, the auto document feeder does not seem to send an end of document notification so gscan2pdf keeps scanning air for a couple of pages before erroring out.  I expect both these problems to be fixed, but until then, I have a work around ...

Here is a script I have tested to convert a multi-page document into a single pdf.  Save it as /usr/local/bin/scan-base and sudo ln -s /usr/local/bin/scan-base /usr/local/bin/scan-pdf.  Then just type scan-pdf into a terminal whenever you want to create a pdf document.  It will drop the image into your home directory.  You will need to adjust the --device-name parameter to that provided by HPLIP.  The reason why this works and gscan2pdf doesn't is I am using the tiff format for scan images.  The default pbm format appears to be what is used by gscan2pdf, and that cannot be processed by convert.  You need imagemagick and ghostscript installed at least for this script to work.

```

#!/bin/bash

# This stop on first error; unfortunately convert complains
# so we can not use it at present (scanimage output images have errors)
# set -e;

# This complains if we try to use unset variables.
set -u;

INVOKE=`basename "$0"`  # can be scan-copy; scan-pdf; scan-copy-pdf; scan-pnm
USER=`whoami`    # user
PROCESSID=$$    # process id for uniqueness
DATETIME=`date +%Y%m%d_%H%M%S`
TMPDIR="/tmp/scan_${USER}_${DATETIME}_${PROCESSID}"
PDFILE="$HOME/scan_${DATETIME}_${PROCESSID}.pdf"

if [ ! -d "${HOME}" ] || [ ! -x "${HOME}" ] || [ ! -d "${HOME}" ]; then
  echo "${INVOKE}: \$HOME environment variable does not appear to"
  echo "${INVOKE}: be properly set.  Make sure it points to your"
  echo "${INVOKE}: home directory, e.g. type: export HOME='/home/me'."
  echo "${INVOKE}: Exiting."
  exit 0
fi

function MKTMP {
  if [ -a "${TMPDIR}" ]; then
    echo "Temporary directory for scan already exists!"
    echo "  ( ${TMPDIR} )"
    echo "  ABORTING!"
    exit 0
  fi  
  mkdir -p "${TMPDIR}"
  if [ ! -r "${TMPDIR}" ]; then
    echo "Cannot create temporary directory for scan!"
    echo "  ( $TMPDIR )"
    echo "  ABORTING!"
    exit 0
  fi  
}

function SCANIT () {
  echo -n "How many pages? ";
  read count;

  # TODO See scanimage -L to get list of devices.
  # May wish to have user select on start

  /usr/bin/scanimage \
    --device-name='hpaio:/net/Officejet_Pro_8600?ip=192.168.1.2' \
    -l 0 -t 0 -x 215.9 -y 279.4 \
    --source=ADF --batch=scan%02d.tiff --batch-count ${count} \
    --format=tiff --mode=color --resolution=300;
}

function CONVERTIT () {
  convert -density 300x300 -geometry 2550x3300 *.tiff out.ps;
  ps2pdf out.ps out.pdf;
}

function PRINTIT () {
  ls *.pnm |while read -r LINE
  do
    BASE=`basename "${LINE}" ".pnm"`;
    convert "${LINE}" "${BASE}.ps";
    lpr -P hp8600 "${BASE}.ps";
  done
}

function CLEANUP () {
  if [ -r "out.pdf" ]; then
    mv out.pdf "${PDFILE}"
  fi  
  cd "${HOME}"
  rm -rf "${TMPDIR}"
}

case $INVOKE in  
  scan-copy)
    MKTMP; cd "${TMPDIR}"; SCANIT; PRINTIT; CLEANUP
  ;;    
  scan-pdf)
    MKTMP; cd "${TMPDIR}"; SCANIT; CONVERTIT; CLEANUP
  ;;  
  scan-copy-pdf)
    MKTMP; cd "${TMPDIR}"; SCANIT; CONVERTIT; CLEANUP
  ;;  
  scan-img)
    MKTMP; cd "${TMPDIR}"; SCANIT
    cd "${HOME}"; mv "${TMPDIR}" ./ ;;
  *)  
    echo "command $INVOKE not supported by scan-simple"
  ;;  
esac
exit 0

```
Why exactly do you use these settings?:
"-l 0 -t 0 -x 215.9 -y 279.4" and not "-x 210 -y 297"

---

### Post by TheOnlyChosenOne on 2013-10-20
> **PJSingh5000 said:**
> z_mikowski,

Thanks so much for sharing your experience and the script.

I was also looking forward to multi page scan capabilities using the printer's auto-feeder. So this is a disappoinement.  I wonder if they will update the driver to allow multi-page scan to work??

Regarding merging individual PDFs, I like to use the PDFmod because it has an easy to use GUI.
Multi page scan works.
```
scanimage --device-name='hpaio:/net/Officejet_Pro_8600?ip=$ip' --batch=output%d.tiff --batch-count $count --format=tiff --resolution 300 --mode=color --source ADF
```

---

### Post by TheOnlyChosenOne on 2013-10-20
> **PJSingh5000 said:**
> This is good to hear.  Do you know if the card reader works as well?
Yes, it does.

---

### Post by mole84 on 2014-06-01
All functions are working for me on ubuntu 13.10 with the HP Officejet Pro 8600 plus.

All over wireless network.

I did have to install HPLIP Toolbox to get the multi-page scan working over wireless. Setup the printer with fax in the HPLIP toolbox.

For the memory card you have to use Places > Connect to Server > smb://xxx.xxx.xxx.xxx ip address of printer. Use the user / password of the admin user on the printer.

---

### Post by PJSingh5000 on 2014-06-03
mole84,

Thanks for the update!

---

