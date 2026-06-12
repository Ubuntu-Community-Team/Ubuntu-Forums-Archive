---
title: "Epson R300 CD Printing with glabels"
date: 2008-09-15
forum: Hardware
---

### Post by purple melon on 2008-09-15
Hi

Does anyone have a Glabels template for printing directly to the cd tray on an Epson Stylus R300 Photo printer or can explain how to edit an existing template to accommodate the R300 cd tray?

I can print to the tray using the  cd-print-canon-hub-templates.xml template but the text is always in the wrong place? and am not sure how to edit the .xml file to suit the R300 tray size and position.

any help appreciated as this is one of the last things stopping me ditching XP completely!   

rgds
P melon

---

### Post by DoctorMO on 2008-09-17
This will require you to do a bit of trial and error. I recommend getting a cd that isn't printable and print on that (then you can wipe away the results when they're wrong)

Post the xml here so I can see it and perhaps change it for you.

But you'll need to find how far out it is, for this you need to create an image which has a black border around the edge and the middle of the cd, create a vertical line and a horizontal line running across the middle of the cd, make one of the thicker than the other a note down which one.

Print this out and then measure how far from the edge the line is off by, both X and Y, make sure to use the lines to orientate the cd correctly.

---

### Post by purple melon on 2008-09-19
Hi

Thanks for your reply DoctorMO

This is what I'm attempting to print with Glabels.

[IMG]http://www.rgc262.ndo.co.uk/image/cdprint.jpeg[/IMG]


This is the print from the cd tray.

[IMG]http://www.rgc262.ndo.co.uk/image/cdtray.jpeg[/IMG]


This is the Glabels template file.

<?xml version="1.0"?>
<Glabels-templates xmlns="http://snaught.com/glabels/2.0/">
  <Template name="CanonPIXMA-directCD" size="Other" width="131mm" height="239mm" description="Canon PIXMA direct CD printing">
    <Label-cd id="0" radius="2.325in" hole="58.5pt" waste="0pt">
      <Layout nx="1" ny="1" x0="5mm" y0="70mm" dx="4.425in" dy="4.625in"/>
      <Markup-margin size="9pt"/>
    </Label-cd>
  </Template>
</Glabels-templates>

As you can see I only get one line printed on the cd and am not sure which lines to edit in the xml file above.

any help appreciated, ta.

---

### Post by DoctorMO on 2008-09-19
Shouldn't there be circles? I advise using the idea in my original email with the outlines.

---

### Post by purple melon on 2008-09-19
Sorry DoctorMO

Didn't put circles on the Glabel template, will do that tomorrow.


thanks for the prompt reply.

---

### Post by DoctorMO on 2008-09-19
Good, don't forget to make one of the lines fatter so you know the orientation (or a different colour)

Once you have the offsets to apply, make your changes to this line:

<Layout nx="1" ny="1" x0="5mm" y0="70mm" dx="4.425in" dy="4.625in"/>

The dx/dy should stay the same (they are the size), but the x0 and y0 are the center co-ordinates.

---

### Post by purple melon on 2008-09-20
Hi

Thanks to DoctorMO I now have the ability to print directly to CD on the Epson R300  with gLabels.

This is the print from the cd tray now
[IMG]http://www.rgc262.ndo.co.uk/image/cdtray1.jpeg[/IMG] 

This is the template file used.

```
<?xml version="1.0"?>
<Glabels-templates xmlns="http://snaught.com/glabels/2.0/">
  <Template name="Epson Stylus Photo R300" size="Other" width="135mm" height="295mm" description="Epson R300 direct CD printing">
    <Label-cd id="0" radius="60mm" hole="58.5pt" waste="0pt">
      <Layout nx="1" ny="1" x0="-2mm" y0="-2mm" dx="4.425in" dy="4.625in"/>
      <Markup-margin size="9pt"/>
    </Label-cd>
 </Template>
</Glabels-templates>
```

A big thanks to DoctorMO


Just need to go clean out the printer now LOL

---

### Post by DoctorMO on 2008-09-20
Now that you have your new template, try and contact the glabels people and contribute your hard work back to them. Give them the model and driver for your printer and see if we can make sure this problem doesn't crop up again.

And don't forget to thank me (it's nice to have the votes) just click the little medal in the bottom/right

---

