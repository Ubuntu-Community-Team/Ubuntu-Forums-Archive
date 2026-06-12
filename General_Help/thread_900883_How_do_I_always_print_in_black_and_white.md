---
title: "How do I always print in black and white?"
date: 2008-08-25
forum: General Help
---

### Post by feedmecereal on 2008-08-25
With my old printer, I just went to the "Printers" window, right-clicked, clicked on "Properties," click "Advanced," and then changed to color model to black and white. With my new printer, I can only select RGB color model.

How to I get my printer to always print in black and white system-wide?

---

### Post by rax_m on 2008-08-27
Normally you go to System->Administration->Printing. Choose your printer and under some of the options, perhaps Printout mode you may see the option to set it to greyscale. 
Of course I'm not sure if this varies with different printers. Which printer do you have?

---

### Post by prshah on 2008-08-27
> **feedmecereal said:**
> 
How to I get my printer to always print in black and white system-wide?

Open the CUPS admin page in a browser: ```
http://127.0.0.1:631
```, then click "Manage Printers", then, under the concerned printer's heading, click "Set printer options" (you may have to scroll to the right side), then, under "Color Model", choose "Greyscale".

---

### Post by feedmecereal on 2008-08-27
The color model is set to RGB and there are no other options to select. I am using a Canon MP210.

---

### Post by prshah on 2008-08-28
> **feedmecereal said:**
> The color model is set to RGB and there are no other options to select. I am using a Canon MP210.

Can you post a screenshot, with the combo box for "color model" open, so that we can see what options are available? Open up the CUPS page, navigate to your printer settings page, then use Applications-Accessories-Take Screenshot, set a delay of 5 (?) seconds, click OK/Take screenshot, click the color model combo box to open it, and wait for the screenshot to be taken; you will be prompted for a save filename when done.

Please upload that file here.

---

### Post by feedmecereal on 2008-08-28
Here you go. It only shows RGB.

---

### Post by BXCracer on 2008-08-28
I have the very same printer and problem, maybe canon is lazy enough ant they havent added support for grayscale printing for linux. I think we have to write to canon and ask to update drivers

Edit: I found the solution. Instead of the mp210 printer driver use Canon PIXMA MP150 - CUPS+Gutenprint. This driver will allow you to print grayscale

---

