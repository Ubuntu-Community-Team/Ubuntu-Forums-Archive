---
title: "[HOWTO] Show Amarok cover in Conky"
date: 2008-07-24
forum: General Help
---

### Post by Askelon on 2008-07-24
Hi!

[[img]http://img371.imageshack.us/img371/5118/capture32ph2.th.jpg[/img]](http://img371.imageshack.us/my.php?image=capture32ph2.jpg)

Yep, it's done! Since conky doesn't provide image support, I decided to write a little program that would help me getting my Amarok cover on my desk as well as other informations like artist or title :) It's actually pretty simple ; I based my work on some pieces of conky's sources, to display the cover image on a small window, at a position we specify, as for the refresh delay.

There's still a few points to be improved :
+ I failed to make the window sticky, you still can move it with Alt+right clic ; 
+ big issue is that the window can only be displayed on one desk, whereas conky can be displayed on all desks ; 
+ the window still appears on windows list Alt+Tab

That's some details that can be meliorate, feel free if you a nice way to it :)

So, here is the code, writen in C :

```
/*
   *
   *                        acd.c
   *                       -------
   *                 Amarok Cover Display
   *             21st July 2008 - Charlie Merland
   *                charlie.merland@gmail.com
   *             ----------------------------
   *
   *  Utility: displays Amarok cover Image at argv[1] delay,
   *  at position given in argv[2] and argv[3].
   *
   *  Use: ./acd 5 25 25
   *
   *  Compilation: this program uses Xlib to display the window
   *  and Imlib2 to display the cover. You must have Imlib2 installed,
   *  and you need to add the flags to the compilation command:
   *
   *      cc acd.c -lX11 -lImlib2 -o acd
   *
   *
   *  Feel free to use/modify/share this code, I made it in that intention =)
   *
   *      
*/

#include <stdio.h>
#include <string.h>
#include <unistd.h>
#include <Imlib2.h>
#include <X11/Xlib.h>
#include <X11/Xatom.h>
#include <X11/Xutil.h>
#include <X11/Xmd.h>

#include "acd.h"


int main( int argc, char **argv )
{
	int inter = atoi( argv[1] );
	int pos_x = atoi( argv[2] );
	int pos_y = atoi( argv[3] );
	char cmd[30] = "dcop amarok player coverImage";
	char cmd_status[26] = "dcop amarok player status";
	char path[128];
	char *fin;
	
	/* put here the color of the "border" around the cover, depending on your
	   own wallpaper. Here I use grey, since my wallpaper is very dark */
	unsigned long bg_color = 0x505050;

	FILE *fd;
	Atom xa, xa_prop;
	

	/* checking Amarok status : if running and actually playing a song */
	fd=popen(cmd_status,"r");
	if(!fd)
	{
		fprintf(stderr,"Error popen\nQuitting.\n" );
		return 1;
	}

	/* we get Amarok status using dcop */
	if(!fgets(path,128,fd))
	{
		fprintf(stderr,"Error fgets\nQuitting.\n" );
		return 1;
	}

	/* here I was testing if Amarok was actually running, but as a matter of facts,
	   if it's not, dcop request failed, making fgets fail too and stop */
	/*if(strstr(path,"ERROR")!=NULL)
	{
		fprintf(stderr,"Error: Amarok is not running");
		return 1;
	}
	else */if(strstr(path,"0")!=NULL)
	{
		printf("Amarok status is 0 : not playing\nQuitting.\n");
		return 1;
	}
	
	
	// checking necessary arguments
	if( argc < 3 )
	{
		printf("  Usage: ./acd intervalle x y");
		printf("  Exemple: ./acd 10 580 480");
		return 1;
	}
	
	/* define the display to use, the screen, etc, */
	/* and get the root windows. Basic Xlib programming. */
	Display *display = XOpenDisplay( NULL );
	int screen = DefaultScreen( display );
	Visual *visuel = DefaultVisual( display, screen );
	Colormap colormap = DefaultColormap( display, screen );

	Window fenetre_root = RootWindow( display, screen );

	/* we set the attibutes, create the windows and make a grey background */
	XSetWindowAttributes attrs = {  ParentRelative, 0L, 0, 0L, 0, 0,
					Always, 0L, 0L, False, ExposureMask | OwnerGrabButtonMask, 0L, True, 0, 0 };
	
	Window fenetre = XCreateWindow(display, fenetre_root, pos_x, pos_y, 154, 154, 0,
				       CopyFromParent, InputOutput, CopyFromParent, CWEventMask, &attrs);
	
	XSetWindowBackground(display, fenetre, bg_color);

	/* Imlib */
	Imlib_Load_Error *error_return;
	Imlib_Image cover;
		
	imlib_context_set_display(display);
	imlib_context_set_visual(visuel);
	imlib_context_set_colormap(colormap);
	imlib_context_set_drawable(fenetre);
	
	/* window display */
	XMapWindow( display, fenetre );	
	XSelectInput( display, fenetre, ExposureMask | OwnerGrabButtonMask );
	
	/* kicking window's decorations */
	xa = ATOM(_MOTIF_WM_HINTS);
	long prop2[5] = { 2, 0, 0, 0, 0 };
	XChangeProperty(display, fenetre, xa, xa, 32, PropModeReplace, (unsigned char *) prop2, 5);
	
	/* move */
	XMoveWindow(display, fenetre, pos_x, pos_y);
	
	for(;;)
	{
		/* skipping taskbar  */
		xa = ATOM(_NET_WM_STATE);
		xa_prop = ATOM(_NET_WM_STATE_SKIP_TASKBAR);
		XChangeProperty(display, fenetre, xa, XA_ATOM, 32, PropModeAppend, (unsigned char *) &xa_prop, 1);
		
		/* window above all others */
		XLowerWindow(display, fenetre);
		
		/* get cmd  command result */
		fd = popen(cmd,"r");
		if(!fd)
		{
			fprintf(stderr,"Error popen\nQuitting.\n");
			return 1;
		}
		
		if(!fgets(path,128,fd))
		{
			fprintf(stderr,"Error fgets\nQuitting.\n" );
			return 1;
		}
		
		fin = strrchr(path, '\n');
		if(fin != NULL) *fin = '\0';
		
		/* load, resize and show the cover */
		cover = imlib_load_image_with_error_return(path,error_return);
		if(!cover)
		{
			printf("Error %d loading image : %s\nQuitting.\n", *error_return, error[*error_return]);
			return 1;
		}

		imlib_context_set_image(cover);
		imlib_render_image_on_drawable_at_size(2,2,150,150);
		
		/*wait... */
		usleep(inter*50000);
		
		pclose(fd);
	}
	
	/* and destroy the window */
	XDestroyWindow(display,fenetre);
	return 0;
}
```


As mentioned in comments, this program uses Xlib and Imlib2, you must have it installed and adapt compilation command :

```
sudo apt-get install libimlib2 libimlib2-dev

cc acd.c -lX11 -lImlib2 -o acd
```

Well, that's it, hope it will be useful to someone =)


PS: so sorry for my (very) poor english skills :oops:

---

### Post by pbeesley on 2008-08-12
Thanks for this I'll give it a go sometime this week. And your english is fine. Better than some Americans I know xD

---

### Post by Askelon on 2008-08-18
Hi!

Thank you pbeesley for your message :)

The project changed a lot those last 3 weeks! It seemed that a lot of people would rather use Rhythmbox than Amarok ; I met a folk on ubuntu-fr.org who's now working with me on it and who did the work to adapt my code to Rhythmbox. We decided to join our two programs into one which aim will be to simply display the cover of the player we choose. We humbly named the project "Cid", Conky Image Display.

I changed the graphical part, now we only use Gtk+-2.0 to manage the window and the cover image. We cut the code in a few files, which will allow the support of various player. I made the Amarok part, for now Amarok only uses DCOP, which is pretty easy to manipulate in C, using popen. But some players like Rhythmbox use Dbus, so the other guy made a part adding Dbus suppor to Cid. I'll adapt his work when Amarok 2 will be stable and so will use Dbus to.

The great advantage we see is that now, if we want to add support for another player, we just need to add a file to sources, and make a function that returns the image's path in a char. The base of the program is pretty well done, and will display the image pointed by the path :)


... Huh, don't know if I'm really clear, hope so :lol: a download/install script is available [here](ftp://ftp.freezee.org/download.sh), and we're now thinking about making the project more "popular", maybe launching a website for the support or somethind like that.

We'll keep you informed ;)

Greatings, Askelon =)

---

### Post by cvid on 2008-08-19
hey ... thnx for ur efforts ... the code in the first post needs acd.h ... can you post that .... secondly, the download script link u provided requires ftp authentication ... can u fix that

---

### Post by kedde on 2008-08-26
Hey on google I found this link for acd.h

[http://forum.ubuntu-fr.org/viewtopic.php?pid=1955142](http://forum.ubuntu-fr.org/viewtopic.php?pid=1955142)

```

#define ATOM(a) XInternAtom(display, #a, False)

char *error[15] = 
{
   "IMLIB_LOAD_ERROR_NONE",
   "IMLIB_LOAD_ERROR_FILE_DOES_NOT_EXIST",
   "IMLIB_LOAD_ERROR_FILE_IS_DIRECTORY",
   "IMLIB_LOAD_ERROR_PERMISSION_DENIED_TO_READ",
   "IMLIB_LOAD_ERROR_NO_LOADER_FOR_FILE_FORMAT",
   "IMLIB_LOAD_ERROR_PATH_TOO_LONG",
   "IMLIB_LOAD_ERROR_PATH_COMPONENT_NON_EXISTANT",
   "IMLIB_LOAD_ERROR_PATH_COMPONENT_NOT_DIRECTORY",
   "IMLIB_LOAD_ERROR_PATH_POINTS_OUTSIDE_ADDRESS_SPACE",
   "IMLIB_LOAD_ERROR_TOO_MANY_SYMBOLIC_LINKS",
   "IMLIB_LOAD_ERROR_OUT_OF_MEMORY",
   "IMLIB_LOAD_ERROR_OUT_OF_FILE_DESCRIPTORS",
   "IMLIB_LOAD_ERROR_PERMISSION_DENIED_TO_WRITE",
   "IMLIB_LOAD_ERROR_OUT_OF_DISK_SPACE",
   "IMLIB_LOAD_ERROR_UNKNOWN"
};

```

---

### Post by abhiroopb on 2009-10-01
Hi is there any update on this project?

---

### Post by WResiak on 2009-11-06
Hi Askelon,
after compiling and running in terminal I can see gray square for few seconds (no cover art) and that 
error output in terminal:

```
witek@witek-desktop:/bin$ ./acd 5 25 25
Segmentation fault (core dumped)
```
 
Do you know reason for it and hopefully solution?

---

### Post by Ziirish on 2010-08-30
Hi.

To answer the previous question, the project is still alive and known as "CID".
You can follow it at [http://cid.ziirish.info/](http://cid.ziirish.info/) (in french) and [http://tracker.ziirish.info/projects/cid](http://tracker.ziirish.info/projects/cid) (in french too).

I am now the main developer and I try to keep it alive as far as I can.

You can also meet me on IRC #cid-fr@freenode, I'll be happy to answer your questions.

Any kind of help is highly welcome ;)

Regards,

Ziirish

---

