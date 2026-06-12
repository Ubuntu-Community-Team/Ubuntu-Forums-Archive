---
title: "What do I do with this GTK file I downloaded?"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by sharrakor on 2009-04-04
I downloaded this GTK file so it would give me the same font as XP (been looking at it for so many years its a bit hard to let go of)... But I don't know what to do with it. It has no extension and didn't come with a readme. I got it off gnome-look.

Here it is:

```

# Ignore the colour descriptions in the comments - they're wrong.
style "clearlooks-default"
{
  GtkButton      ::default_border    = { 0, 0, 0, 0 }
  GtkRange       ::trough_border     = 0
  GtkPaned       ::handle_size       = 6
  GtkRange       ::slider_width      = 15
  GtkRange       ::stepper_size      = 15
  
  GtkScrollbar   ::min_slider_length = 30
  GtkCheckButton ::indicator_size    = 14
  GtkMenuBar     ::internal-padding  = 0
  GtkTreeView    ::expander_size     = 14
  GtkExpander    ::expander_size     = 16
  GtkScale       ::slider-length     = 27
  #GtkToolbar     ::button-relief     = GTK_RELIEF_NORMAL
  #GtkMenuBar     ::shadow-type       = GTK_SHADOW_OUT
  #GtkScrollbar   ::has-forward-stepper = 0
  #GtkScrollbar   ::has-backward-stepper = 0
  #GtkScrollbar   ::has-secondary-backward-stepper = 1
  
  xthickness = 1
  ythickness = 1

  fg[NORMAL]            = "#000000"
  fg[PRELIGHT]          = "#000000"
  fg[ACTIVE]            = "#000000"
  fg[SELECTED]          = "#ffffff"
  fg[INSENSITIVE]       = "#777777"
  
  bg[NORMAL]            = "#ece9d8"
  bg[PRELIGHT]          = "#f5f2e0"
  bg[ACTIVE]            = "#d4d1c2"
  bg[SELECTED]          = "#2a5cab"
  bg[INSENSITIVE]       = "#d4d1c2"

  base[NORMAL]          = "#ffffff"
  base[PRELIGHT]        = "#f5f2e0"
  base[ACTIVE]          = "#d4d0c8"
  base[SELECTED]        = "#316ac5"
  base[INSENSITIVE]     = "#d4d0c8"

  text[ACTIVE]          = "#000000"
  text[PRELIGHT]        = "#000000"
  text[SELECTED]        = "#ffffff"

  engine "candido" 
  {
	scrollbar_color   = "#aec8f7"
    menubarstyle      = 0 # 0 = flat, 1 = sunken, 2 = flat gradient
    menuitemstyle     = 1 # 0 = flat, 1 = 3d-ish (gradient), 2 = 3d-ish (button)
    listviewitemstyle = 1 # 0 = flat, 1 = 3d-ish (gradient)
    progressbarstyle  = 1 # 0 = candy bar, 1 = fancy candy bar, 2 = flat
    animation         	= TRUE
  }
}


style "clearlooks-wide" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 2
}

style "clearlooks-wider" = "clearlooks-default"
{
  xthickness = 3
  ythickness = 3
}

style "clearlooks-button" = "clearlooks-wider"
{
  bg[NORMAL]        = "#f3f3ef"
  bg[INSENSITIVE]   = "#f3f3ef"
  bg[PRELIGHT]      = "#ffffff"
}

style "clearlooks-notebook" = "clearlooks-wide"
{
  bg[NORMAL]      = "#ece9d8"
  bg[INSENSITIVE] = "#ece9d8"
  bg[SELECTED]    = "#ffc73c"
}

style "clearlooks-tasklist" = "clearlooks-default"
{
  xthickness = 5
  ythickness = 3
}

style "clearlooks-menu" = "clearlooks-default"
{
  xthickness = 3
  ythickness = 2
  bg[NORMAL] = "#ffffff"
  fg[NORMAL] = "#ffffff"
  text[NORMAL] = "#ffffff"
}

style "clearlooks-menu-item" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 3
  fg[PRELIGHT] = "#ffffff"
  fg[NORMAL] = "#000000"
  bg[PRELIGHT] = "#2a5cab"
}

style "clearlooks-menubar" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 2
}

style "clearlooks-tree" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 2
}

style "clearlooks-frame-title" = "clearlooks-default"
{
  fg[NORMAL] = "#404040"
}

style "clearlooks-tooltips" = "clearlooks-default"
{
  xthickness = 4
  ythickness = 4
  bg[NORMAL] = { 1.0,1.0,0.75 }
}

style "clearlooks-progressbar" = "clearlooks-wide"
{
  xthickness = 1
  ythickness = 1
  fg[PRELIGHT]  = "#ffffff"
}

style "clearlooks-combo" = "clearlooks-button"
{
}

# widget styles
class "GtkWidget"      style "clearlooks-default"
class "GtkButton"      style "clearlooks-button"
class "GtkScale"       style "clearlooks-button"
class "GtkCombo"       style "clearlooks-button"
class "GtkRange"       style "clearlooks-wide"
class "GtkFrame"       style "clearlooks-wide"
class "GtkMenu"        style "clearlooks-menu"
class "GtkEntry"       style "clearlooks-wider"
class "GtkMenuItem"    style "clearlooks-menu-item"
class "GtkNotebook"    style "clearlooks-notebook"
class "GtkProgressBar" style "clearlooks-progressbar"
class "*MenuBar*"      style "clearlooks-menubar"

widget_class "*MenuItem.*" style "clearlooks-menu-item"

# combobox stuff
widget_class "*.GtkComboBox.GtkButton" style "clearlooks-combo"
widget_class "*.GtkCombo.GtkButton"    style "clearlooks-combo"
# tooltips stuff
widget_class "*.tooltips.*.GtkToggleButton" style "clearlooks-tasklist"
widget "gtk-tooltips" style "clearlooks-tooltips"

# treeview stuff
widget_class "*.GtkTreeView.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCTree.GtkButton" style "clearlooks-tree"
widget_class "*.GtkList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkFrame.GtkLabel" style "clearlooks-frame-title"

# notebook stuff
widget_class "*.GtkNotebook.*.GtkEventBox" style "clearlooks-notebook"
widget_class "*.GtkNotebook.*.GtkViewport" style "clearlooks-notebook"


```

I would have posted in the Absolute Beginners section, but it appears that it is down for now. I've got no idea what type of code it is so I'm not sure how to run/complie it. Could someone please enlighten me?

---

### Post by cariboo on 2009-04-04
Why not install the mscorefonts package that is available in the repositories? I would suggest you install the the ubuntu-restricted-extras meta package, as it will also install flash, java and codecs to play most audio/video media. The meta package is in the repositories and you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim

---

### Post by sharrakor on 2009-04-04
Thanks. Ubuntu is no longer painful to look at :)

Out of curiosity though, do you know what the code I posted was for/what language its in?

---

