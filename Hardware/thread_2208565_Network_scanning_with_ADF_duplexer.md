---
title: "Network scanning with ADF duplexer"
date: 2014-03-01
forum: Hardware
---

### Post by Ck.asdf on 2014-03-01
I just purchased a Brother MFC-J870DW.

I have followed the prerequisites on [this page]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html").

I've installed the 64 bit versions of the following from [this page]("http://welcome.solutions.brother.com/bsc/public/us/us/en/dlf/download_index.html?reg=us&c=us&lang=en&prod=mfcj870dw_us_eu_as&dlid=&flang=English&os=128&type2=-1") using the provided instructions:
LPR printer driver
CUPSwrapper printer driver
Scanner driver
Scan-key-tool
Scanner Setting file

I have network printing working, and with some help [from here]("http://askubuntu.com/questions/383568/multiple-page-scan-using-scanimage"), network scanning using the ADF and scanimage.  Xsane didn't work with multiple pages, and simple-scan would crash upon initiating the scan.

However, duplex scanning isn't working yet.

I found this helpful thread here:
[http://ubuntuforums.org/showthread.php?t=1671216](http://ubuntuforums.org/showthread.php?t=1671216)

The thread suggests getting help from scanimage to provide device-specific details.  These are listed below.

(Code with "[...]" has been trimmed to lessen distraction.)

```

ck@ck:/stor/downloads/brother$ scanimage --help --device-name "brother4:net1;dev0"
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write image data to
standard output.

Parameters are [...]

scanimage: rounded value of br-x from 215.9 to 215.88
scanimage: rounded value of br-y from 355.6 to 355.567

Options specific to device `brother4:net1;dev0':
  Mode:
    --mode Black & White|Gray[Error Diffusion]|True Gray|24bit Color|24bit Color[Fast] [24bit Color[Fast]]
        Select the scan mode
    --resolution [...]
    --[COLOR="#FF0000"]**source FlatBed|Automatic Document Feeder(left aligned)|Automatic Document Feeder(left aligned,Duplex)|Automatic Document Feeder(centrally aligned)|Automatic Document Feeder(centrally aligned,Duplex) [Automatic Document Feeder(left aligned)]**[/COLOR]
        Selects the scan source (such as a document-feeder).
    --brightness [...]
    --contrast [...]
  Geometry:
    -l [...]
    -t [...]
    -x [...]
    -y [...]

```

In the other thread, their printer's duplex option was "--ScanMode Duplex" though mine appears to be what I highlighted in red above, starting with "--source" - however, when I use the below, for example, it just pretends like it's a single-sided document.

scanimage --source "Automatic Document Feeder(left aligned,Duplex)"
or
scanimage --source "Automatic Document Feeder(centrally aligned,Duplex)"

I've even tried
scanimage --source "left aligned,Duplex"
but then it complains that I've provided an invalid argument (no complaints by the system for the longer versions above).

Thoughts on what I may be doing wrong above?

Thanks for any help you can provide! :)

---

### Post by Ck.asdf on 2014-03-16
Any thoughts?

---

