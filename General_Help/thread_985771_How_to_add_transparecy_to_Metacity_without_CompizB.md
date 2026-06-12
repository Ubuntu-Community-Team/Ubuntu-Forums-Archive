---
title: "How to add transparecy to Metacity without Compiz/Beryl"
date: 2008-11-17
forum: General Help
---

### Post by hakuchi18 on 2008-11-17
some wat noob here... I have ubuntu 8.10, I have tried compiz-fusion with beryl but nevr managed to get it working after reading many forums.. I have metacity as my compositing manager it has enabled a shadow effect behind all my windows but what i wish to have is transparency on windows, pop boxes and so on. My system monitor seems to have a transparent background to it. Just to inform that i did noting to any files or options to enable this. my desktop effects are set to none, but if i disable metacy as the windows manger i lose the shadow effect and the transparency to system monitor. If this was enable to password request dialog and the system monitor why not evrything else?:confused:

Heres wat i mean
[IMG]http://i270.photobucket.com/albums/jj84/lvalen17/SystemMonitortransparent.jpg[/IMG]

---

### Post by hictio on 2008-11-18
As I understand, the option to enable Metacity's own composite capabilities is reachable thru gconf-editor, and you can find it on:

```

/apps/metacity/general/compositing_manager

```

---

### Post by ShodanjoDM on 2008-11-18
The transparency of non-Compiz enabled desktop that you see came from the new Murrine GTK2 theme engine. As of present most of the applications still don't have support for the engine's transparency feature.

The system monitor is one of the application that already has it, there are some others, exaile for example, that you have to recompile it yourself with additional patches.

Look [[COLOR="Orange"]here[/COLOR]]("http://www.cimitan.com/murrine/rgba-support/list") for a more complete list of the applications with RGBA support (whether it's already implemented or with patches / plugins).

---

### Post by hakuchi18 on 2008-11-18
thats were i enabled metacity at.. i also noticed that the theme "Darkroom" is the only theme that adds the transparency to some of the system apps but all other themes just have a solid background. So its the theme i guess that adds the transparency but im still wonder if there is an app out there that would enable transparency.

---

### Post by ShodanjoDM on 2008-11-18
> **hakuchi18 said:**
> thats were i enabled metacity at.. i also noticed that the theme "Darkroom" is the only theme that adds the transparency to some of the system apps but all other themes just have a solid background. So its the theme i guess that adds the transparency but im still wonder if there is an app out there that would enable transparency.

There's a hidden option in Murrine based themes' gtkrc file. This example is from my modified Dust theme:

```

	engine "murrine" 
	{
		animation           = TRUE  # FALSE = disabled, TRUE = enabled
		colorize_scrollbar  = TRUE  # FALSE = disabled, TRUE = enabled
		contrast            = 1.0   # 0.8 for less contrast, more than 1.0 for more contrast on borders
		glazestyle          = 0     # 0 = flat highlight, 1 = curved highlight, 2 = concave style, 3 = top curved highlight, 4 = beryl highlight
		gradient_shades     = {1.1,1.0,1.0,0.87} # default: {1.1,1.0,1.0,1.1}
		gradients           = TRUE  # FALSE = disabled, TRUE = enabled
		highlight_ratio     = 1.0  # set highlight amount for buttons or widgets
		lightborder_ratio   = 1.0   # sets lightborder amount for buttons or widgets
		lightborderstyle    = 0     # 0 = lightborder on top side, 1 = lightborder on all sides
		listviewheaderstyle = 1     # 0 = flat, 1 = glassy, 2 = raised
		listviewstyle       = 0     # 0 = nothing, 1 = dotted
		menubaritemstyle    = 0     # 0 = menuitem look, 1 = button look
		menubarstyle        = 1     # 0 = flat, 1 = glassy, 2 = gradient, 3 = striped
		menuitemstyle       = 1     # 0 = flat, 1 = glassy, 2 = striped
		menustyle           = 0     # 0 = no vertical menu stripe, 1 = display vertical menu stripe
		reliefstyle	    = 2     # 0 = flat, 1 = inset, 2 = shadow
		[COLOR="Red"]rgba		    = TRUE  # FALSE = disabled, TRUE = enabled[/COLOR]
		roundness           = 2     # 0 = squared, 1 = old default, more will increase roundness
		scrollbarstyle      = 2     # 0 = nothing, 1 = circles, 2 = handles, 3 = diagonal stripes, 4 = diagonal stripes and handles, 5 = horizontal stripes, 6 = horizontal stripes and handles
		sliderstyle         = 0     # 0 = nothing added, 1 = handles
		stepperstyle        = 1     # 0 = standard, 1 = integrated stepper handles, 2 = unknown
		style		    = MURRINE # engine style options: CANDIDO, CLEARLOOKS, MIST, MURRINE, NODOKA
		toolbarstyle	    = 0     # 0 = flat, 1 = glassy, 2 = gradient
	}
```

Most murrine based themes - especially the older ones - don't have that option. Sometimes even the newer ones have it disabled.

You can add the rgba option yourself by editing the gtkrc file with text editor.

---

### Post by hakuchi18 on 2008-11-18
> **ShodanjoDM said:**
> There's a hidden option in Murrine based themes' gtkrc file. This example is from my modified Dust theme:

```

	engine "murrine" 
	{
		animation           = TRUE  # FALSE = disabled, TRUE = enabled
		colorize_scrollbar  = TRUE  # FALSE = disabled, TRUE = enabled
		contrast            = 1.0   # 0.8 for less contrast, more than 1.0 for more contrast on borders
		glazestyle          = 0     # 0 = flat highlight, 1 = curved highlight, 2 = concave style, 3 = top curved highlight, 4 = beryl highlight
		gradient_shades     = {1.1,1.0,1.0,0.87} # default: {1.1,1.0,1.0,1.1}
		gradients           = TRUE  # FALSE = disabled, TRUE = enabled
		highlight_ratio     = 1.0  # set highlight amount for buttons or widgets
		lightborder_ratio   = 1.0   # sets lightborder amount for buttons or widgets
		lightborderstyle    = 0     # 0 = lightborder on top side, 1 = lightborder on all sides
		listviewheaderstyle = 1     # 0 = flat, 1 = glassy, 2 = raised
		listviewstyle       = 0     # 0 = nothing, 1 = dotted
		menubaritemstyle    = 0     # 0 = menuitem look, 1 = button look
		menubarstyle        = 1     # 0 = flat, 1 = glassy, 2 = gradient, 3 = striped
		menuitemstyle       = 1     # 0 = flat, 1 = glassy, 2 = striped
		menustyle           = 0     # 0 = no vertical menu stripe, 1 = display vertical menu stripe
		reliefstyle	    = 2     # 0 = flat, 1 = inset, 2 = shadow
		[COLOR="Red"]rgba		    = TRUE  # FALSE = disabled, TRUE = enabled[/COLOR]
		roundness           = 2     # 0 = squared, 1 = old default, more will increase roundness
		scrollbarstyle      = 2     # 0 = nothing, 1 = circles, 2 = handles, 3 = diagonal stripes, 4 = diagonal stripes and handles, 5 = horizontal stripes, 6 = horizontal stripes and handles
		sliderstyle         = 0     # 0 = nothing added, 1 = handles
		stepperstyle        = 1     # 0 = standard, 1 = integrated stepper handles, 2 = unknown
		style		    = MURRINE # engine style options: CANDIDO, CLEARLOOKS, MIST, MURRINE, NODOKA
		toolbarstyle	    = 0     # 0 = flat, 1 = glassy, 2 = gradient
	}
```

Most murrine based themes - especially the older ones - don't have that option. Sometimes even the newer ones have it disabled.

You can add the rgba option yourself by editing the gtkrc file with text editor.


I checked all the themes that came with ubuntu and the theme DarkRoom was the only one that had RGBA in the file and set to True. So all i need to do i guess is check with the themes gtkrc file and enable rgba. Thanks alot

---

