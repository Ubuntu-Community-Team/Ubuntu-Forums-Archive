---
title: "Dymo LabelWriter Duo; printing to tapes"
date: 2020-05-30
forum: Hardware
---

### Post by Keith_Beef on 2020-05-30
I intend this as a follow-up to [an older, closed, thread]("https://ubuntuforums.org/showthread.php?t=861781").

I recently dug out my old Dymo LabelWriter Duo because I want to print some high-visibility tapes to stick onto various containers (acetone, isopropyl alcohol, quenching oil etc.) and materials (X115CrV3, X42CrMo4 etc.), and so on...

I downloaded the latest version of the Dymo SDK, compiled and installed it, and set up two printers in CUPS: one for the label printer, one for the tape printer.

Everything went well. The last time I went through all this, the label printer worked easily enough, but the tape printer wouldn't work. This time, both are working, but the tape printer is out of alignment, and I have to go through an extra steps of printing to a PDF file, first.

In glabels, I created a 1" high x 4" wide template in normal orientation. I used this template to create a label with one line of text "centered text" centred both vertically and horizontally within a box covering the whole of the template area (NOT just within the margins).

From previous attempts, I found out that I needed to print first to a PDF file, leaving all the settings as default.

Then I print the PDF from evince, to the tape printer, using the following parameters:
	Paper type: 	24mm (1")
	Paper size: 	24mm (1") continuous
	Orientation:	Portrait

The text appears on the tape, but below the centre and far to the left.

Below is the XML of my template.
```
<?xml version="1.0"?>
<Glabels-templates xmlns="http://glabels.org/xmlns/3.0/">
  <Template brand="Dymo" part="Tape 1&quot;x4&quot;" size="Other" width="101.6mm" height="25.4mm" description="Tape 1&quot; wide for a 4&quot; long label">
    <Label-rectangle id="0" width="88.9mm" height="25.4mm" round="0mm" x_waste="0mm" y_waste="0mm">
      <Markup-margin size="3.175mm"/>
      <Layout nx="1" ny="1" x0="0mm" y0="0mm" dx="88.9mm" dy="25.4mm"/>
    </Label-rectangle>
  </Template>
</Glabels-templates>
```

Any advice would be much appreciated.

---

