---
title: "Success! Wacom with dual monitors on Karmic"
date: 2009-12-29
forum: Hardware
---

### Post by Robbie Huffman on 2009-12-29
Luckily for me the driver worked "out of the box", but the dual display setup did not. Circles drawn one the pad came out as ovals on the screen, or else the pad mapped to the entire virtual desktop, making responsiveness very bad.

But finally! Thanks to a number of posts on the forums here and the man page for 'wacom', I have the file below. I saved it as /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi and re-plugged in the tablet.

The big trick was to change the TVResolution to contain the correct sizes for my screens. Plus it was not obvious which was first and which was second, so I had to swap them until it worked. Also, the Twinview setting had to be 'leftof', which surprised me.

```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="input.x11_options.KeepShape" type="string">off</merge>
        <merge key="input.x11_options.Twinview" type="string">leftof</merge>
        <merge key="input.x11_options.TVResolution" type="string">1280x1024,1680x1050</merge>
        <merge key="info.product" type="string">stylus</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
          <append key="wacom.types" type="strlist">cursor</append>
          <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="eraser">
      <merge key="info.product" type="string">eraser</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="cursor">
      <merge key="info.product" type="string">cursor</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="pad">
      <merge key="info.product" type="string">pad</merge>
    </match>
  </device>
</deviceinfo>


```

---

### Post by mtoddedwads on 2009-12-30
I'm trying to set up an X41 Tablet (Wacom) with dual monitors on Karmic.  I tried using your fdi file without success (the pen still moves the cursor across both screens, whereas I want to pen to only work with the Wacom "side").

Any thoughts?  What kind of videocard do you have?  NVidia perhaps?  I believe my laptop has an Intel 910.

---

### Post by mtoddedwads on 2009-12-30
Okay, I got the dual monitors to work with my X41 Wacom-based tablet (more or less).  THANK YOU for your idea!  It seems that I had to explicitly add an extra line specifying the screen number (this seems odd to me, since I'd think that Screen 0 would be the default).

<merge key="input.x11_options.KeepShape" type="string">off</merge>
<merge key="input.x11_options.Twinview" type="string">leftof</merge>
<merge key="input.x11_options.TVResolution" type="string">1024x800,1680x1050</merge>
<merge key="input.x11_options.ScreenNo" type="string">0</merge>

After I restarted X, it worked.

> sudo /etc/init.d/gdm restart

Note that if I move too far to the right of the "tablet screen", the pen controls the cursor on the "wrong" screen (the non-tablet screen).  In this case, the cursor has a difficult time "jumping back" to the "tablet side".  This is remedied by tapping on the extreme upper left corner of the tablet screen (which causes the cursor to jump back).  I'd love to know how to "force" the pen to stay on the tablet screen.

---

### Post by Robbie Huffman on 2009-12-30
mtoddedwads,

There is one more setting - MMonitor. Check the Wacom manpage. It's not clear to me what you would change the setting to, but it reads like putting in a 0 would limit the tablet to the first screen, and a 1 to the second screen. For this setting, you would also have to change TwinView to 'none'.

<merge key="input.x11_options.Twinview" type="string">none</merge>
<merge key="input.x11_options.MMonitor" type="string">0</merge>

Let us know how it turns out!

---

### Post by Cenema on 2010-01-16
Hi, I have a dual monitor and use a wacom bamboo tablet with nvidia twinview: I tried to follow instructions of this post and others to make it work. Eventually my tablet is working without any strange behaviour but it is still mapped to both screens and trying to map it to one only it's driving me crazy!
Can somebody help me? Here's my linuxwacom.fdi file:

```
<?xml version="1.0" encoding="ISO-8859-1"?>

<!-- Wacom:  tablets, tablet pc's, and touch screen laptops -->
<deviceinfo version="0.2">
  <!-- for all Wacom USB tablets -->
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Wacom">
	<merge key="input.x11_options.KeepShape" type="string">off</merge>
	<merge key="input.x11_options.Twinview" type="string">leftof</merge>
	<merge key="input.x11_options.TVResolution" type="string">1366x768</merge>
	<merge key="input.x11_options.ScreenNo" type="string">0</merge>
	<merge key="input.x11_options.Twinview" type="string">none</merge>
	<merge key="input.x11_options.MMonitor" type="string">off</merge>
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
	<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	<append key="wacom.types" type="strlist">eraser</append>
	<append key="wacom.types" type="strlist">cursor</append>
	<append key="wacom.types" type="strlist">pad</append>
        <!-- for HP dv3-2250 multi-touch laptop -->
        <match key="info.udi" contains="e2">
          <merge key="input.x11_options.Type" type="string">touch</merge>
        </match>
      </match>
    </match>
  </device>
  <!-- for most Wacom USB tablets with touch -->
  <device>
    <match key="input.originating_device" contains="if1">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">touch</merge>
        <!-- for Bamboo Pen & Touch tablets -->
	<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	<append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
  </device>
  <!-- for Wacom Serial tablets -->
  <device>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf;FUJ02e5;FUJ02e7">
	<append key="info.capabilities" type="strlist">input</append>
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
	<merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
	<merge key="input.device" type="copy_property">serial.device</merge>
	<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	<append key="wacom.types" type="strlist">eraser</append>
	<append key="wacom.types" type="strlist">cursor</append>
	<!-- Serial tablets with touch capabilities -->
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009;WACf010;WACf008A;WACf00B;WACf00C;WACf00D;WACf00E;FUJ02e7">
	  <append key="wacom.types" type="strlist">touch</append>
	</match>
        <!-- Serial tablets that operate at higher baud rate -->
        <match key="@info.parent:pnp.id" contains_outof="WACf008">
          <merge key="input.x11_options.BaudRate" type="string">38400</merge>
        </match>
      </match>
    </match>
  </device>
  <!-- Match the Wacom Bluetooth A5 pen tablet -->
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="WACOM">
        <match key="info.product" contains="Tablet">
          <merge key="input.x11_driver" type="string">wacom</merge>
          <merge key="input.x11_options.Type" type="string">stylus</merge>
	  <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	  <append key="wacom.types" type="strlist">eraser</append>
	  <append key="wacom.types" type="strlist">cursor</append>
        </match>
      </match>
    </match>
  </device>
  <!-- Wacom names "parser" -->
  <device>
    <match key="info.udi" contains_not="subdev_0">
    <match key="info.udi" contains_not="subdev_1">
    <match key="info.udi" contains_not="subdev_2">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="info.product" type="string">stylus</merge>
      </match>
      <match key="input.x11_options.Type" contains="eraser">
        <merge key="info.product" type="string">eraser</merge>
      </match>
      <match key="input.x11_options.Type" contains="cursor">
        <merge key="info.product" type="string">cursor</merge>
      </match>
      <match key="input.x11_options.Type" contains="pad">
        <merge key="info.product" type="string">pad</merge>
      </match>
      <match key="input.x11_options.Type" contains="touch">
        <merge key="info.product" type="string">touch</merge>
      </match>
    </match>
    </match>
    </match>
  </device>
</deviceinfo>

```

---

### Post by Favux on 2010-01-16
Hi Cenema,

See if moving your monitor options to below the stylus line and above the info.callout line makes a difference.  Right now they are above the wacom driver line.

---

### Post by Cenema on 2010-01-16
Thank you for answering :) 
I modified this part of the file.fdi and it didn't work (bit I post it because I'm quite sure I've been dumb enough to make something wrong):
```
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Wacom">
	<merge key="input.x11_options.KeepShape" type="string">off</merge>
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
	<merge key="input.x11_options.Twinview" type="string">leftof</merge>
	<merge key="input.x11_options.TVResolution" type="string">1366x768</merge>
	<merge key="input.x11_options.ScreenNo" type="string">0</merge>
	<merge key="input.x11_options.Twinview" type="string">none</merge>
	<merge key="input.x11_options.MMonitor" type="string">off</merge>
	<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	<append key="wacom.types" type="strlist">eraser</append>
	<append key="wacom.types" type="strlist">cursor</append>
	<append key="wacom.types" type="strlist">pad</append>
        <!-- for HP dv3-2250 multi-touch laptop -->
        <match key="info.udi" contains="e2">
          <merge key="input.x11_options.Type" type="string">touch</merge>
        </match>
      </match>
    </match>

```
I also tried to do something with wacomcpl but I have two problems: the "Screen mapping" option is always set to "none" as I reboot xdm and, if I change it to Vertical (or Horizontal), and set it to screen 0, nothing happens

---

### Post by Favux on 2010-01-16
Hi Cenema,

As far as I know these are the 3 basic lines you need:
```
          <merge key="input.x11_options.TwinView" type="string">Horizontal</merge>
          <merge key="input.x11_options.TVResolution" type="string">1440x900,1280x1024</merge>
          <merge key="input.x11_options.ScreenNo" type="string">0</merge>
```
Notice in TV resolution you have to specify both monitors.

In Jaunty there was a "bug" in Nvidia dual screen setup.  You needed to run nvidia-settings as root.
```
gksudo nvidia-settings
```
Using TwinView, put the monitors where you want them.  In X Server Display Configuration->set position to Absolute if screens re not the same resolution, or use Left Of, Right Of if they are.  Enter Apply and then Save to X Configuration File.  This should make the settings permanent.  If you do it from the Desktop Nvidia X Server Settings the configuration isn't saved (although it should be) because you're not root.

But I think it was fixed in Karmic.

---

