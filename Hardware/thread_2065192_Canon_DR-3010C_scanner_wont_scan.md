---
title: "Canon DR-3010C scanner wont scan"
date: 2012-10-01
forum: Hardware
---

### Post by sanderDrost on 2012-10-01
Hello,

I'm trying to use the canon DR-3010C with SANE. I've tried about all possible fixes i have found to get it to work but the scanner hasn't made a single sound at every attempt. Does anyone know what would be the next best thing to look into to get this thing to scan?

The Canon DR-3010C is shown as untested in the available scanners list. I have been unable to find a SANE specific forum and the irc channel is useless.

EDIT: solved it, got in contact with a developer of the sane project.

---

### Post by m_pav on 2012-10-21
Care to share how you actually got it going?

---

### Post by sanderDrost on 2012-10-23
Hi

For those who are having the same problem with this scanner heres what i did to make it work with scanimage. You will need to install the canon_dr backend with a little adjustment.

Download the backend here: [http://www.sane-project.org/snapshots/](http://www.sane-project.org/snapshots/)

Unzip and go to the 'backends' directory, in there find 'canon_dr.c'. Open this file and search for the method, 'init_model()'. In this method you will see a bunch of the dr-models in an if(), else if() statement.

else if (strstr (s->model_name,"DR-2510")), etc. the DR-3010 is not among them so i coppied the whole scope of the DR-2510 and changed 2510 to 3010. (the code is below here, you can just copy that) 

To make it work, this is what the developer told me and it worked, you will need the s->invert_tly = 1 flag. Note that this is commented out with the 2510. It will look like this:

```
else if (strstr (s->model_name,"DR-3010"))
{
    s->rgb_format = 1;
    s->always_op = 0;
    s->unknown_byte2 = 0x80;
    s->fixed_width = 1;
    s->valid_x = 8.5 * 1200;
    s->gray_interlace[SIDE_FRONT] = GRAY_INTERLACE_2510;
    s->gray_interlace[SIDE_BACK] = GRAY_INTERLACE_2510;
    s->color_interlace[SIDE_FRONT] = COLOR_INTERLACE_2510;
    s->color_interlace[SIDE_BACK] = COLOR_INTERLACE_2510;
    s->duplex_interlace = DUPLEX_INTERLACE_2510;
    s->duplex_offset = 400;
    s->need_ccal = 1;
    s->need_fcal = 1;
    s->sw_lut = 1;
    s->invert_tly = 1;

    /*only in Y direction, so we trash them in X*/
    s->std_res_x[DPI_100]=0;
    s->std_res_x[DPI_150]=0;
    s->std_res_x[DPI_200]=0;
    s->std_res_x[DPI_240]=0;
    s->std_res_x[DPI_400]=0;

    /*lies*/
    s->can_halftone=0;
    s->can_monochrome=0;
}
```

Save the file like this.

Now go to the top directory of the backend in the terminal and type:

"BACKENDS=canon_dr ./configure --prefix=/usr --sysconfdir=/etc &#8211;localstatedir=/var"

then:

"make"
(this may take a while)

then:

"sudo make install"

The backend is now installed. Check if (in the terminal) "scanimage -L" finds the scanner, else turn it off and back on. If the scanner is found try putting a paper in it and type "scanimage -T" to test the scanner.

If it still doesn't work you might want to try changing the permissions on the usb port. if "scanimage -L" shows "'device `canon_dr:libusb:005:004' is a CANON DR-3010C scanner" then type:

sudo chmod a+w /dev/bus/usb/005/004

-----

The solution aint perfect yet, not all the flags coppied in the code from the 2510C are needed for the 3010C (i only know s->invert_tly = 1 is needed as it didnt scan without it) but i havent had time to finetune and test it properly.

Nevertheless, i hope this is helpfull for those having the same problem and that im not forgetting anything important.

If it doesnt work, let me know and ill try my best to help.

---

### Post by sanderDrost on 2012-11-08
"BACKENDS=canon_dr ./configure --prefix=/usr --sysconfdir=/etc &#8211;localstatedir=/var"

has to be

"BACKENDS=canon_dr ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var"

---

