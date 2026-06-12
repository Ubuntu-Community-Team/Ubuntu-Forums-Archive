---
title: "How do I open up a docx file?"
date: 2008-10-02
forum: General Help
---

### Post by askyourpc.com on 2008-10-02
I get email attachments that are a docx files. I think the file type is associated with Microsoft Office 2007 and they don't seem to open up with Open Office. Anyone know of a good converter or Microsoft Office 2007 clone? Or is their a way to update Open Office to be able to understand docx files?

Thanks

---

### Post by drs305 on 2008-10-02
The following will allow running a command to convert docx files into openoffice files. The procedures are taken from the following link but correct one error and account for an older library. OpenOffice will include built-in support in 3.0.

[Convert OpenXML (.docx, etc.) in Linux using command line]("http://www.oooninja.com/2008/01/convert-openxml-docx-etc-in-linux-using.html")

Download the rpms:
32-Bit:
```

wget http://download.go-oo.org/red-carpet/ooo-680/sled-10-sp-i586/odf-converter-1.1-7.i586.rpm

```
64-Bit:
```

http://download.go-oo.org/red-carpet/ooo-680/sled-10-sp-x86_64/odf-converter-1.1-7.x86_64.rpm

```

Assuming your download directory is ~/Desktop. If not, change the command to your download directory.
```

cd ~/Desktop

```

Unpackage the rpm. This will create opt and usr folders in Desktop:
```

rpm2cpio odf-converter*rpm | cpio -ivd

```

Copy the binary (32-bit):
```

sudo cp usr/lib/ooo-2.0/program/OdfConverter /usr/bin

```

Copy the binary (64-bit):  Note the original link is in error regarding 64-bit installation.
```

sudo cp usr/lib**_64_**/ooo-2.0/program/OdfConverter /usr/bin
cp 

```

Delete the opt and usr folders in Desktop if desired.

There may be a problem running the script as it appears to call libtiff.so.3 while libtiff4 is now standard in the repositories. To overcome this, with libtiff4 installed, create a symbolic link:
```

sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3 

```

To convert a docx file:
```

OdfConverter /i example.docx

```

---

