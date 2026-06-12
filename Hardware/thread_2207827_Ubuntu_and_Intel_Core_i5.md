---
title: "Ubuntu and Intel Core i5"
date: 2014-02-25
forum: Hardware
---

### Post by rafael-cordano on 2014-02-25
Hello,
I've an Intel Core i5(3337U) with Ubuntu 13.10 and I notice that goes a slow, has ubuntu a version optimaized for intel i5?

Thanks
Rafael Cordano

---

### Post by open2reason on 2014-02-25
Rafael,
Does your computer run slow when comparing with other versions of Ubuntu you have used or runs slow when compared to other Inter cpus you have used?

---

### Post by rafael-cordano on 2014-02-25
Runs faster with Wind..., and is a laptop. Other versions of ubuntu runs in the same velocity.
I believe that linux is not optimized for intel i5.
PD: The laptop model is Acer Aspire M5-582PT, has 6gb of ram, intel HD 4000 graphics.

Thanks
Rafael Cordano

---

### Post by open2reason on 2014-02-25
Rafael,
Would it be possible for you to run Dash > System Testing application after first making sure you do not have any updates or other tasks running in the background? 
The report generated may well draw your attention to any parts of your system that may require further attention so as to bring them up to your expectations.
The application GtkPerf (to be found in the repos) could also be run so as to give you another metric of system performance.

ATB

---

### Post by rafael-cordano on 2014-02-25
Gtk Perf results are:
GtkPerf 0.40 - Starting testing: Tue Feb 25 12:01:34 2014


GtkEntry - time:  0,05
GtkComboBox - time:  0,61
GtkComboBoxEntry - time:  0,42
GtkSpinButton - time:  0,12
GtkProgressBar - time:  0,13
GtkToggleButton - time:  0,12
GtkCheckButton - time:  0,08
GtkRadioButton - time:  0,08
GtkTextView - Add text - time:  0,14
GtkTextView - Scroll - time:  0,10
GtkDrawingArea - Lines - time:  0,27
GtkDrawingArea - Circles - time:  0,27
GtkDrawingArea - Text - time:  0,16
GtkDrawingArea - Pixbufs - time:  0,01
 --- 
Total time:  2,59

---

### Post by open2reason on 2014-02-25
Rafael,
Your results are way faster than mine :( but that is life.

Does the System Testing show any areas that may be of better arranged by adding new drivers, versions of applications or other such?

Do you have any applications that you suspect of running slower under 13.10 than than other releases as they may throw light upon areas of concern?

---

### Post by ajgreeny on 2014-02-25
Do you use the integrated graphics card on the CPU or have you a separate graphic card as well using optimus hybrid graphics, which can cause big problems in Linux.

There is certainly no problem in general with Intel i5 CPUs; I run an i5-3570K with HD4000 graphics and it runs like a demon with Xubuntu 12.04, but I use only the integrated graphics chip.  Out of interest my gtkperf score is around 1.56
```
GtkEntry - time:  0.00
GtkComboBox - time:  0.26
GtkComboBoxEntry - time:  0.14
GtkSpinButton - time:  0.02
GtkProgressBar - time:  0.01
GtkToggleButton - time:  0.02
GtkCheckButton - time:  0.02
GtkRadioButton - time:  0.03
GtkTextView - Add text - time:  0.38
GtkTextView - Scroll - time:  0.04
GtkDrawingArea - Lines - time:  0.27
GtkDrawingArea - Circles - time:  0.25
GtkDrawingArea - Text - time:  0.11
GtkDrawingArea - Pixbufs - time:  0.01
 --- 
Total time:  1.56
```and I do not think your score is what would be considered slow either, so I just wonder if it is unity that is causing your problem.

---

### Post by Yellow Pasque on 2014-02-25
> **rafael-cordano said:**
> has ubuntu a version optimized for intel i5?

The 64-bit version is what you should be using.

---

### Post by IvoGuerreiro on 2014-02-25
Hi,
i use a 64 bit version in my inter core i5-430 processor, and ubuntu 13.10, run perfectly.

---

### Post by rafael-cordano on 2014-02-25
I've only integrated graphics, and I've ubuntu 64 bits.
I was reading on people that need an optimaized linux for i3 i5 and i7 and says something of sse4.2.

Thanks

---

### Post by grahammechanical on 2014-02-25
You may need to activate a different video Driver. Ubuntu comes with a fallback video driver that does run the desktop slowly. The fallback is designed for older machines that do not have video cards that can run accelerated graphics in the video card. Sometimes the fallback video mode will run when we do not need it. For example, it will run if we boot into Recovery Mode>Resume.

Go to System Settings>Software and Updates>Additional Drivers tab. Allow Ubuntu time to find some drivers for you and then experiment.

Regards.

---

