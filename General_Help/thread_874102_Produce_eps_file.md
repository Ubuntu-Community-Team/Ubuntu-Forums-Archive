---
title: "Produce eps file?"
date: 2008-07-29
forum: General Help
---

### Post by svensta on 2008-07-29
How can I setup a virtual printer that can produce eps (encapsulated postscript) files?
I would be like to be able to choose this printer in any SW that can print, like OpenOffice and Gimp. If eps isn't possible, then ps could also be acceptable.
TIA

---

### Post by eldragon on 2008-07-29
i asume you want eps to include in latex documents?

ive always used inkscape to export eps files.

not what you are looking for, but close enough, good luck

---

### Post by coffeecat on 2008-07-29
In Open Office, go to Help > OpenOffice.org Help > Index and search for PostScript. I'm afraid the instructions are not exactly straightforward.

As far as the Gimp is concerned, my 'Beginning GIMP' (by Akkana Peck, Apress and well worth getting) says that you need the Gimp-Print, now called Gutenprint, plugin. There's a 'gimp-gutenprint' package in Synaptic, so I guess that's what you need.

I realise that this was not really what you were asking for.

---

### Post by mannheim on 2008-07-29
In OpenOffice, I saving as ps is easy. In the Print dialog, check "Print to File". This will save as a ps file. (At least, that's how it works with both my printers.)

You will probably then want to use another utility to convert ps to eps. I think ghostscript must be able to do this. I know that imagemagick can do it with the command-line "convert foo.ps foo.eps".

---

