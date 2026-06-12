---
title: "Maverick Meerkat, Nvidia-96 and Compiz"
date: 2010-10-07
forum: Hardware
---

### Post by christian.remboldt on 2010-10-07
If you are using the proprietary Nvidia legacy driver 96 when you upgrade to 10.10 Xorg wont load.

Solution: Remove all nvidia packages and replace with xserver-xorg-video-nouveau. You will also need to make changes to /etc/X11/xorg.conf.

With the new xorg almost everything is auto configured so a very simple xorg.conf is sufficient. He is a copy of mine.

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nouveau"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Once X is started with the nouveau driver, everything else can be configured with gnome-display-properties. Gnome uses RandR by default. So If you are using dual monitors like me you will easily be able to set them up with this.

On to compiz and desktop effects. 3d isn't officially supported for nouveau, but it still seems to work pretty well.

You need packages libgl1-mesa-glx and libdrm-nouveau1 for sure. Also maybe libkms1 and a few others. I have a lot of drm and mesa packages installed. So I'm not 100% sure which packages are needed but a few extra packages usually wont hurt anything.

Finally you need the 3d driver this file is not included in any package. /usr/lib/dri/nouveau_vieux_dri.so

How to build nouveau_vieux_dri.so

git clone git://anongit.freedesktop.org/git/mesa/mesa
cd /mesa
./autogen.sh
./configure --with-dri-drivers=nouveau
make

This will result in /mesa/lib/nouveau_vieux_dri.so Copy this file to /usr/lib/dri and restart. Then you should be able to enable desktop effects from System>Preferences>Appearance Visual Effects tab.

If you don't want to build it yourself, here is a link to the one I built yesterday. [http://www.mediafire.com/?bzszrsej376y8q7](http://www.mediafire.com/?bzszrsej376y8q7)

I think when 10.10 goes live on Sunday more people will be experiencing issues with this. If you have any additions please drop a line, or questions. I might be able to help.

---

### Post by bluestar14 on 2010-10-10
k, my mesa folder doesnt have a configure file, so ./configure wont run

---

### Post by yo2boy on 2010-10-10
Currently not on Ubuntu but I was very very mad at Ubuntu nVidia driver not showing up in "Additional Drivers" I'll have to re-install 10.10 because I messed up something and now a console screen shows up. So I always have to use Recovery Mode

---

### Post by cgroza on 2010-10-10
Thanks MAN! You rock. No longer need the proprietary ones.

---

### Post by christian.remboldt on 2010-10-15
@bluestar14 

I'm sorry I forgot you need to run ./autogen.sh before ./configure --with-dri-drivers=nouveau. I added it to the first post. but thought you might not see my edit.

@yo2boy

Reinstalling 10.10 wont do anything. There are currently no "additional drivers" for nvidia-96 cards. You should try and follow my walkthrough.

---

### Post by messenjer on 2010-10-16
To compile you need these packages

aptitude install git autoconf xutils-dev libtalloc-dev libdrm-dev x11proto-dri2-dev x11proto-gl-dev libxmu-dev

---

### Post by messenjer on 2010-10-16
I have this error when I try to compile :

nouveau_context.c:131: error: too many arguments to function ‘nouveau_channel_alloc’

May be a bug in the development version, I'll try later...

---

### Post by christian.remboldt on 2010-10-16
nouveau_context.c has been changed 4 times since I compiled. So there is a good chance one of those broke it.

[http://cgit.freedesktop.org/mesa/mesa/log/src/mesa/drivers/dri/nouveau/nouveau_context.c](http://cgit.freedesktop.org/mesa/mesa/log/src/mesa/drivers/dri/nouveau/nouveau_context.c)

thats the git log. you can try and role back the four changes or use this from 9/30/10


```
/*
 * Copyright (C) 2009-2010 Francisco Jerez.
 * All Rights Reserved.
 *
 * Permission is hereby granted, free of charge, to any person obtaining
 * a copy of this software and associated documentation files (the
 * "Software"), to deal in the Software without restriction, including
 * without limitation the rights to use, copy, modify, merge, publish,
 * distribute, sublicense, and/or sell copies of the Software, and to
 * permit persons to whom the Software is furnished to do so, subject to
 * the following conditions:
 *
 * The above copyright notice and this permission notice (including the
 * next paragraph) shall be included in all copies or substantial
 * portions of the Software.
 *
 * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
 * EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
 * MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
 * IN NO EVENT SHALL THE COPYRIGHT OWNER(S) AND/OR ITS SUPPLIERS BE
 * LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
 * OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
 * WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
 *
 */

#include "nouveau_driver.h"
#include "nouveau_context.h"
#include "nouveau_bufferobj.h"
#include "nouveau_fbo.h"

#include "main/dd.h"
#include "main/framebuffer.h"
#include "main/light.h"
#include "main/state.h"
#include "drivers/common/meta.h"
#include "drivers/common/driverfuncs.h"
#include "swrast/swrast.h"
#include "swrast/s_context.h"
#include "vbo/vbo.h"
#include "tnl/tnl.h"
#include "tnl/t_context.h"

#define need_GL_EXT_framebuffer_object
#define need_GL_EXT_fog_coord
#define need_GL_EXT_secondary_color

#include "main/remap_helper.h"

static const struct dri_extension nouveau_extensions[] = {
	{ "GL_ARB_multitexture",	NULL },
	{ "GL_ARB_texture_env_add",	NULL },
	{ "GL_ARB_texture_mirrored_repeat", NULL },
	{ "GL_EXT_fog_coord",		GL_EXT_fog_coord_functions },
	{ "GL_EXT_framebuffer_blit",	NULL },
	{ "GL_EXT_framebuffer_object",	GL_EXT_framebuffer_object_functions },
	{ "GL_EXT_packed_depth_stencil", NULL},
	{ "GL_EXT_secondary_color",	GL_EXT_secondary_color_functions },
	{ "GL_EXT_stencil_wrap",	NULL },
	{ "GL_EXT_texture_env_combine",	NULL },
	{ "GL_EXT_texture_filter_anisotropic", NULL },
	{ "GL_EXT_texture_lod_bias",	NULL },
	{ "GL_NV_blend_square",         NULL },
	{ "GL_NV_texture_env_combine4",	NULL },
	{ NULL,				NULL }
};

static void
nouveau_channel_flush_notify(struct nouveau_channel *chan)
{
	struct nouveau_context *nctx = chan->user_private;
	GLcontext *ctx = &nctx->base;

	if (nctx->fallback < SWRAST)
		nouveau_bo_state_emit(ctx);
}

GLboolean
nouveau_context_create(gl_api api,
		       const __GLcontextModes *visual, __DRIcontext *dri_ctx,
		       void *share_ctx)
{
	__DRIscreen *dri_screen = dri_ctx->driScreenPriv;
	struct nouveau_screen *screen = dri_screen->private;
	struct nouveau_context *nctx;
	GLcontext *ctx;

	ctx = screen->driver->context_create(screen, visual, share_ctx);
	if (!ctx)
		return GL_FALSE;

	nctx = to_nouveau_context(ctx);
	nctx->dri_context = dri_ctx;
	dri_ctx->driverPrivate = ctx;

	return GL_TRUE;
}

GLboolean
nouveau_context_init(GLcontext *ctx, struct nouveau_screen *screen,
		     const GLvisual *visual, GLcontext *share_ctx)
{
	struct nouveau_context *nctx = to_nouveau_context(ctx);
	struct dd_function_table functions;
	int ret;

	nctx->screen = screen;
	nctx->fallback = HWTNL;

	/* Initialize the function pointers. */
	_mesa_init_driver_functions(&functions);
	nouveau_driver_functions_init(&functions);
	nouveau_bufferobj_functions_init(&functions);
	nouveau_texture_functions_init(&functions);
	nouveau_fbo_functions_init(&functions);

	/* Initialize the mesa context. */
	_mesa_initialize_context(ctx, visual, share_ctx, &functions, NULL);

	nouveau_state_init(ctx);
	nouveau_bo_state_init(ctx);
	_mesa_meta_init(ctx);
	_swrast_CreateContext(ctx);
	_vbo_CreateContext(ctx);
	_tnl_CreateContext(ctx);
	nouveau_span_functions_init(ctx);
	_mesa_allow_light_in_model(ctx, GL_FALSE);

	/* Allocate a hardware channel. */
	ret = nouveau_channel_alloc(context_dev(ctx), 0xbeef0201, 0xbeef0202,
				    &nctx->hw.chan);
	if (ret) {
		nouveau_error("Error initializing the FIFO.\n");
		return GL_FALSE;
	}

	nctx->hw.chan->flush_notify = nouveau_channel_flush_notify;
	nctx->hw.chan->user_private = nctx;

	/* Enable any supported extensions. */
	driInitExtensions(ctx, nouveau_extensions, GL_TRUE);

	return GL_TRUE;
}

void
nouveau_context_deinit(GLcontext *ctx)
{
	struct nouveau_context *nctx = to_nouveau_context(ctx);

	if (TNL_CONTEXT(ctx))
		_tnl_DestroyContext(ctx);

	if (vbo_context(ctx))
		_vbo_DestroyContext(ctx);

	if (SWRAST_CONTEXT(ctx))
		_swrast_DestroyContext(ctx);

	if (ctx->Meta)
		_mesa_meta_free(ctx);

	if (nctx->hw.chan)
		nouveau_channel_free(&nctx->hw.chan);

	nouveau_bo_state_destroy(ctx);
	_mesa_free_context_data(ctx);
}

void
nouveau_context_destroy(__DRIcontext *dri_ctx)
{
	struct nouveau_context *nctx = dri_ctx->driverPrivate;
	GLcontext *ctx = &nctx->base;

	context_drv(ctx)->context_destroy(ctx);
}

void
nouveau_update_renderbuffers(__DRIcontext *dri_ctx, __DRIdrawable *draw)
{
	GLcontext *ctx = dri_ctx->driverPrivate;
	__DRIscreen *screen = dri_ctx->driScreenPriv;
	struct gl_framebuffer *fb = draw->driverPrivate;
	struct nouveau_framebuffer *nfb = to_nouveau_framebuffer(fb);
	unsigned int attachments[10];
	__DRIbuffer *buffers = NULL;
	int i = 0, count, ret;

	if (draw->lastStamp == *draw->pStamp)
		return;
	draw->lastStamp = *draw->pStamp;

	if (nfb->need_front)
		attachments[i++] = __DRI_BUFFER_FRONT_LEFT;
	if (fb->Visual.doubleBufferMode)
		attachments[i++] = __DRI_BUFFER_BACK_LEFT;
	if (fb->Visual.haveDepthBuffer && fb->Visual.haveStencilBuffer)
		attachments[i++] = __DRI_BUFFER_DEPTH_STENCIL;
	else if (fb->Visual.haveDepthBuffer)
		attachments[i++] = __DRI_BUFFER_DEPTH;
	else if (fb->Visual.haveStencilBuffer)
		attachments[i++] = __DRI_BUFFER_STENCIL;

	buffers = (*screen->dri2.loader->getBuffers)(draw, &draw->w, &draw->h,
						     attachments, i, &count,
						     draw->loaderPrivate);
	if (buffers == NULL)
		return;

	for (i = 0; i < count; i++) {
		struct gl_renderbuffer *rb;
		struct nouveau_surface *s;
		int index;

		switch (buffers[i].attachment) {
		case __DRI_BUFFER_FRONT_LEFT:
		case __DRI_BUFFER_FAKE_FRONT_LEFT:
			index = BUFFER_FRONT_LEFT;
			break;
		case __DRI_BUFFER_BACK_LEFT:
			index = BUFFER_BACK_LEFT;
			break;
		case __DRI_BUFFER_DEPTH:
		case __DRI_BUFFER_DEPTH_STENCIL:
			index = BUFFER_DEPTH;
			break;
		case __DRI_BUFFER_STENCIL:
			index = BUFFER_STENCIL;
			break;
		default:
			assert(0);
		}

		rb = fb->Attachment[index].Renderbuffer;
		s = &to_nouveau_renderbuffer(rb)->surface;

		s->width = draw->w;
		s->height = draw->h;
		s->pitch = buffers[i].pitch;
		s->cpp = buffers[i].cpp;

		nouveau_bo_ref(NULL, &s->bo);
		ret = nouveau_bo_handle_ref(context_dev(ctx),
					    buffers[i].name, &s->bo);
		assert(!ret);
	}

	_mesa_resize_framebuffer(NULL, fb, draw->w, draw->h);
}

static void
update_framebuffer(__DRIcontext *dri_ctx, __DRIdrawable *draw,
		   int *stamp)
{
	GLcontext *ctx = dri_ctx->driverPrivate;
	struct gl_framebuffer *fb = draw->driverPrivate;

	*stamp = *draw->pStamp;

	nouveau_update_renderbuffers(dri_ctx, draw);
	_mesa_resize_framebuffer(ctx, fb, draw->w, draw->h);

	/* Clean up references to the old framebuffer objects. */
	context_dirty(ctx, FRAMEBUFFER);
	context_bctx(ctx, FRAMEBUFFER);
	FIRE_RING(context_chan(ctx));
}

GLboolean
nouveau_context_make_current(__DRIcontext *dri_ctx, __DRIdrawable *dri_draw,
			     __DRIdrawable *dri_read)
{
	if (dri_ctx) {
		struct nouveau_context *nctx = dri_ctx->driverPrivate;
		GLcontext *ctx = &nctx->base;

		/* Ask the X server for new renderbuffers. */
		if (dri_draw->driverPrivate != ctx->WinSysDrawBuffer)
			update_framebuffer(dri_ctx, dri_draw,
					   &dri_ctx->dri2.draw_stamp);

		if (dri_draw != dri_read &&
		    dri_read->driverPrivate != ctx->WinSysReadBuffer)
			update_framebuffer(dri_ctx, dri_read,
					   &dri_ctx->dri2.read_stamp);

		/* Pass it down to mesa. */
		_mesa_make_current(ctx, dri_draw->driverPrivate,
				   dri_read->driverPrivate);
		_mesa_update_state(ctx);

	} else {
		_mesa_make_current(NULL, NULL, NULL);
	}

	return GL_TRUE;
}

GLboolean
nouveau_context_unbind(__DRIcontext *dri_ctx)
{
	/* Unset current context and dispath table */
	_mesa_make_current(NULL, NULL, NULL);

	return GL_TRUE;
}

void
nouveau_fallback(GLcontext *ctx, enum nouveau_fallback mode)
{
	struct nouveau_context *nctx = to_nouveau_context(ctx);

	nctx->fallback = MAX2(HWTNL, mode);

	if (mode < SWRAST)
		nouveau_state_emit(ctx);
	else
		FIRE_RING(context_chan(ctx));
}

static void
validate_framebuffer(__DRIcontext *dri_ctx, __DRIdrawable *draw,
		     int *stamp)
{
	struct gl_framebuffer *fb = draw->driverPrivate;
	struct nouveau_framebuffer *nfb = to_nouveau_framebuffer(fb);
	GLboolean need_front =
		(fb->_ColorDrawBufferIndexes[0] == BUFFER_FRONT_LEFT ||
		 fb->_ColorReadBufferIndex == BUFFER_FRONT_LEFT);

	if (nfb->need_front != need_front) {
		nfb->need_front = need_front;
		dri2InvalidateDrawable(draw);
	}

	if (*draw->pStamp != *stamp)
		update_framebuffer(dri_ctx, draw, stamp);
}

void
nouveau_validate_framebuffer(GLcontext *ctx)
{
	__DRIcontext *dri_ctx = to_nouveau_context(ctx)->dri_context;
	__DRIdrawable *dri_draw = dri_ctx->driDrawablePriv;
	__DRIdrawable *dri_read = dri_ctx->driReadablePriv;

	if (ctx->DrawBuffer->Name == 0)
		validate_framebuffer(dri_ctx, dri_draw,
				     &dri_ctx->dri2.draw_stamp);

	if (ctx->ReadBuffer->Name == 0)
		validate_framebuffer(dri_ctx, dri_read,
				     &dri_ctx->dri2.read_stamp);

	if (nouveau_next_dirty_state(ctx) >= 0)
		nouveau_state_emit(ctx);
}
```

---

### Post by beew on 2010-10-17
Hi,

I tried to follow your tutorial but failed at the first step. There is no /etc/X11/xorg.conf. I only have a file called "xorg.conf.dist-upgrade-201010142112" I tried to create one like yours and on restart I booted into the terminal instead of the Desktop, the only way I could get back the Desktop was to remove the xorg.conf file I have created.

Maybe I am missing something?

I have created a thread in the Absolute Beginner Talk section for exactly this problem.
[URL="http://www.uluga.ubuntuforums.org/showthread.php?t=1598591"]
http://www.uluga.ubuntuforums.org/showthread.php?t=1598591[/URL]

Your help would be greatly appreciated.

---

### Post by marfal on 2010-10-17
Many thanks, I now have a 3D desktop on my Toshiba satellite 2410-601 with geforce4 420 go 32mb. I had almost given up when I found this post.

Cheers

---

### Post by Jive Turkey on 2010-10-17
I had major problems when trying this.  I couldn't build the driver (make errors) and using the pre built one from the OP I could not boot.  booting to a root shell and removing the downloded driver from /usr/lib/dri got me back to where I started.

At this time, the nvidia 96 driver still appears to not work for me however the nouveau driver from the repos is acceptable (better than nothing).  This seems to be a regression from 10.04

---

### Post by christian.remboldt on 2010-10-18
@beew, Do you have **only** "xserver-xorg-video-nouveau" installed? Run synaptic package manager and do a search for nvidia.

@Jive Turkey, What architecture are you using? That file is x86. Technically the changes are a progression. 10.10 is now using Xorg1.9. Which is better. You only need to look at the new size of xorg.conf.

---

### Post by beew on 2010-10-19
> **christian.remboldt said:**
> @beew, Do you have **only** "xserver-xorg-video-nouveau" installed? Run synaptic package manager and do a search for nvidia.



Yes, and the graphic is totally screwed up, nevermind 3d. I don't have internet access for that computer now because the broadcom driver is not working either. But if you can please look at the screenshots I posted here.
[URL="http://ubuntuforums.org/showthread.php?t=1598591"]
http://ubuntuforums.org/showthread.php?t=1598591[/URL]

Not being able to create an xorg.conf file seems to be a problem.

---

### Post by Xoanan on 2010-10-21
Hi All

Having another issue with this fix myself.

upon using ./autogen.sh, I receive this.

```
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:15: warning: AC_INIT: not a literal: https://bugs.freedesktop.org/enter_bug.cgi?product=Mesa
autoreconf: configure.ac: tracing
configure.ac:15: warning: AC_INIT: not a literal: https://bugs.freedesktop.org/enter_bug.cgi?product=Mesa
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
configure.ac:15: warning: AC_INIT: not a literal: https://bugs.freedesktop.org/enter_bug.cgi?product=Mesa
autoreconf: configure.ac: not using Autoheader
autoreconf: configure.ac: not using Automake
autoreconf: Leaving directory `.'
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gmake... no
checking for make... make
checking for makedepend... no
checking for sed... /bin/sed
configure: error: makedepend is required to build Mesa
```

I tried to find and install makedepend, but no dice..

any thoughts?

---

### Post by beew on 2010-10-21
I found a different solution, by downgrading xorg.

[http://ubuntuforums.org/showthread.php?t=1598591](http://ubuntuforums.org/showthread.php?t=1598591)

---

### Post by tigang on 2010-10-21
This is quite simply a disaster... all of the ex-Windoze folk I have converted with Nvidia issues are giving up... and I am still struggling after a week.

The Miserable Meerkat is the biggest step backwards in an alternative to Micro$oft I have encountered... it needs to be sorted for the masses NOT the likes of geeks like me... and even I'm struggling! :-(

---

### Post by tigang on 2010-10-21
> **tigang said:**
> This is quite simply a disaster... all of the ex-Windoze folk I have converted with Nvidia issues are giving up... and I am still struggling after a week.

The Miserable Meerkat is the biggest step backwards in an alternative to Micro$oft I have encountered... it needs to be sorted for the masses NOT the likes of geeks like me... and even I'm struggling! :-(

Forgive me folks but... I am trying to help my poor friends who don't know what a 'terminal' is. Booting into MeerKrap at the moment gets them to an old fashioned 'Unix' login prompt. What do I tell them?

---

### Post by beew on 2010-10-21
> **tigang said:**
> Forgive me folks but... I am trying to help my poor friends who don't know what a 'terminal' is. Booting into MeerKrap at the moment gets them to an old fashioned 'Unix' login prompt. What do I tell them?

Try my solution, it works beautifully for me, no need to mess around with configuration files and it uses the Nvidia driver. The only terminal work involved was copying, renaming sources list and editing it by changing all "maverick" to "lucid".

---

### Post by Xoanan on 2010-10-21
I did try it, Beew, but I did encounter some issues..

upon attempting to reinstall nvidia-173
```
E: nvidia-173: subprocess installed post-installation script returned error exit status 10
E: nvidia-173-dev: dependency problems - leaving unconfigured
E: nvidia-173-kernel-source: dependency problems - leaving unconfigured
E: nvidia-glx-173: dependency problems - leaving unconfigured
E: nvidia-glx-173-dev: dependency problems - leaving unconfigured
```

---

### Post by beew on 2010-10-21
> **Xoanan said:**
> I did try it, Beew, but I did encounter some issues..

upon attempting to reinstall nvidia-173
```
E: nvidia-173: subprocess installed post-installation script returned error exit status 10
E: nvidia-173-dev: dependency problems - leaving unconfigured
E: nvidia-173-kernel-source: dependency problems - leaving unconfigured
E: nvidia-glx-173: dependency problems - leaving unconfigured
E: nvidia-glx-173-dev: dependency problems - leaving unconfigured
```

How did you reinstall nvidia-173? Manually using Synaptic (or sudo apt-get install, which is the same thing) or did you let Hardware Drivers do it? (Remember "Additional Drivers" has to be downgraded also to the Lucid version). It didn't work when I tried to do it manually, have to let the downgraded (Lucid) version of "Hardware Drivers" to do the job (otherwise you get "driver activated but not in use" and no 3d effect or Compiz)

Another thing is, make sure you reinstasate the Maverick repo before you attempt to reinstall the nvidia drivers, otherwise you will run into dependency problems. So, Lucid version of xorg and "Hardware Drivers"(jockey) but Maverick repo to fetch the drivers from (and you have to reboot after you downgraded xorg, for otherwise you are still in the Maverick version, that's why you must make sure to have the nouveau driver installed before you reboot, otherwise you will not have any graphic after reboot)

In my system everything else was up to date except for those things that I wanted to downgrade and I have not encountered any dependency problem.

---

### Post by christian.remboldt on 2010-10-21
@Xoanan the package you are missing is xutils-dev, but it still wont compile due to a bug in the CVS unless you revert a few changes. Next this thread is about ONLY the nvidia-96 legacy driver. If your hardware supports the 173-legacy driver, which has already been fixed by nvidia. All you had to do was remove the old driver and install the new one.

@tigang This problem has NOTHING to do with Ubuntu. This issue was recorded long before the release date. In fact I started this thread on the 8th two day before official release. Ubuntu can not be held responsible for the lack of a timely update by NVIDIA.

10.10 is an incremented update and not necessary for general use. The "masses" should stick to LTS releases. If you advised recent converts other than this. You lead them astray and once again Ubuntu cant be held responsible for this.

Additionally if you needed any more evidence for the open source movement you have it in spades. On as side note. I believe this issue is only present with people upgrading form 10.04. Fresh installs of 10.10 should automatically install the nouveau driver(with out 3d support). This is an effort by Ubuntu to remove any need for proprietary software form their distributions. 

Finally your attitude is unappreciated and unneeded. This is software libre, contribute before you criticize. Just because a few users experienced issues, you cant generalize the whole release.

---

### Post by tigang on 2010-10-22
christian.remboldt

All you say is true and I apologise for my unfair comments.

I have been taking the 6-monthly updates since I started using Ubuntu three years ago without a hitch, so I envouraged my friends to do the same. As you said, it is not Ubuntu's fault that Nvidia had not got it act together for the new xorg, but I am still disappointed that the dist upgrade did not disable the defunct Nvidia driver and enable Nouveau so that non-expert users could at least get a working system.

I have used your fix and installed the driver that you so kindly pre-compiled... all works perfectly.

Many thanks and best regards.

---

### Post by beew on 2010-10-22
Christian

While I somehow get my Nvidia card to work I am still mystified by the fact that I don't even have an xorg.conf file and trying to create one takes me to the terminal when reboot. Running startx gives the error message "no screens found", the only way to get back to the Desktop is to remove xorg.conf. Since quite a few people report success with your method I think for them it is not an issue (I started with an upgrade from Lucid, then I did a clean install and ran into the same problem in both instances)

Since this is a test install on an old machine (Inspiron 8500, 2.2 GHZ, 512M of Ram) I wouldn't mind reinstalling just to try out your method so that I can learn something. But it is a no go if I can't even make the first step. 

BTW, I notice video playback is very choppy (for flash and MP4) and cpu usage is always hovering around 100%, --I disable Compiz and put the system on openbox whenever I play videos so it is easier on ram,--I wonder if using your method may improve video performance (the card is GeForce4 Ti 4200 Go AGP 8x)

---

### Post by christian.remboldt on 2010-10-22
@tigang apologies accepted and glad to hear things are working better for you now.
 
@beew video performace will be an issue with the nouveau driver. Without a xorg.conf file xorg does its best to auto configure everything. This may be using the nouveau driver but most likely it is the fail safe fglrx driver. You can check /var/log/Xorg.0.log to see what is happening. If you only get a termianl prompt when booting with xorg.conf, there is a problem with the configurations in this file. I recommend trying my simple xorg.conf and comapring the two log files. Dont use nvidia-xconfig it wont work. The xorg.conf I put in the first post is the xorg.conf.failsafe from xorg 1.7 with fglrx replaced with nouveau

---

### Post by messenjer on 2010-10-22
Current git version is broken. You can download the latest stable version :

```
wget http://cgit.freedesktop.org/mesa/mesa/snapshot/mesa-7.9.tar.gz
tar xzvf mesa-7.9.tar.gz
cd mesa-7.9
./autogen.sh
./configure --with-dri-drivers=nouveau
make
sudo cp lib/nouveau_vieux_dri.so /usr/lib/dri/
```

---

### Post by Xoanan on 2010-10-22
@ChristianRembolt;  Not sure which driver I am supposed to have.  I saw both of them installed when I was using 10.04.  

@beew; thanx and trying again; I'll let you know.:popcorn:

---

### Post by christian.remboldt on 2010-10-22
@messenjer nice call on the snapshot.

@Xoanan You shouldn't have both drivers installed. If your device uses the nvidia-173 driver. Remove the nouveau driver and use the updated version of nvidia-173 from the maverick meerkat repo. 

If you mean you aren't sure which nvidia driver to use. The simplest way to check is to remove all nvidia drivers from your system. Then restart in recovery mode and run /System/Administration/Additional Drivers. If your card is supported by a 173 or newer, it will be installed. If not you need to use nouveau.

For users of the nvidia-96 driver make sure and remove it before switching to nouveau.

---

### Post by John Harrington on 2010-10-22
Which nouveau hardware accelerated 3d driver you need depends on your card.  According to the nouveau website, for nvidia chips from nv30 and up, you need the driver nouveau_dri.so which is in the maverick universe libgl1-mesa-dri-experimental package.  For nvidia chips nv20 and earlier, you need nouveau_vieux_dri.so.

I don't think nouveau-vieux-dri.so is in any maverick package in the official repositories.  It seems to have been removed from libgl1-mesa-dri-experimental before the maverick final release.  However, you don't need to build it.  I got it by adding the xorg-edgers ppa repository:  [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)  

nouveau_vieux_dri.so is in the libgl1-mesa-dri package (not the experimental package, which I don't need at all).  After adding the repository, reloading (using synaptic), installing all updates, and doing a cold reboot (power completely off and then back on), I had accelerated 3d.  Foobillard (a 3d pool simulation) worked just as well as with the nvidia proprietary driver, except that some of the textures looked different.

To determine which nvidia chip you've got, go here:  [http://nouveau.freedesktop.org/wiki/CodeNames](http://nouveau.freedesktop.org/wiki/CodeNames)
I have a GeForce 4 MX card, which corresponds to the NV10 chip.

---

### Post by Xoanan on 2010-10-23
@ChristianRembolt; it looks the 96 driver;
@beew; tried your trick again and it worked! Thanx!!

---

### Post by tigang on 2010-10-24
> **John Harrington said:**
> Which nouveau hardware accelerated 3d driver you need depends on your card.  According to the nouveau website, for nvidia chips from nv30 and up, you need the driver nouveau_dri.so which is in the maverick universe libgl1-mesa-dri-experimental package.  For nvidia chips nv20 and earlier, you need nouveau_vieux_dri.so.

I don't think nouveau-vieux-dri.so is in any maverick package in the official repositories.  It seems to have been removed from libgl1-mesa-dri-experimental before the maverick final release.  However, you don't need to build it.  I got it by adding the xorg-edgers ppa repository:  [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")  

John

Obviously my nvidia chip comes into the <=nv20 category hence Christian's pre-compiled driver working for me. I guess if I'd set the edgers ppa I would not have needed Christian's driver, but as that is working I'll wait until the proprietary nvidia driver is fixed and try that. I am not opposed to the Nouveau driver (especially as it is open source), but the current setup is definitely slower and some Compiz extras are not functioning correctly/at all.

---

### Post by I Am Noob on 2010-10-25
> **christian.remboldt said:**
> If you are using the proprietary Nvidia legacy driver 96 when you upgrade to 10.10 Xorg wont load.

Solution: Remove all nvidia packages and replace with xserver-xorg-video-nouveau. You will also need to make changes to /etc/X11/xorg.conf.

With the new xorg almost everything is auto configured so a very simple xorg.conf is sufficient. He is a copy of mine.

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nouveau"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```Once X is started with the nouveau driver, everything else can be configured with gnome-display-properties. Gnome uses RandR by default. So If you are using dual monitors like me you will easily be able to set them up with this.

On to compiz and desktop effects. 3d isn't officially supported for nouveau, but it still seems to work pretty well.

You need packages libgl1-mesa-glx and libdrm-nouveau1 for sure. Also maybe libkms1 and a few others. I have a lot of drm and mesa packages installed. So I'm not 100% sure which packages are needed but a few extra packages usually wont hurt anything.

Finally you need the 3d driver this file is not included in any package. /usr/lib/dri/nouveau_vieux_dri.so

How to build nouveau_vieux_dri.so

git clone git://anongit.freedesktop.org/git/mesa/mesa
cd /mesa
./autogen.sh
./configure --with-dri-drivers=nouveau
make

This will result in /mesa/lib/nouveau_vieux_dri.so Copy this file to /usr/lib/dri and restart. Then you should be able to enable desktop effects from System>Preferences>Appearance Visual Effects tab.

If you don't want to build it yourself, here is a link to the one I built yesterday. [http://www.mediafire.com/?bzszrsej376y8q7](http://www.mediafire.com/?bzszrsej376y8q7)

I think when 10.10 goes live on Sunday more people will be experiencing issues with this. If you have any additions please drop a line, or questions. I might be able to help.

Hey christian.remboldt,

Right i've read your solution and it seems very similar to another that i've read about... Infact I think the solution came from John who writes on page 3... anyhow, i've been having problems getting Ubuntu 10.10 to recognise my GeForce4 MX460 which is a N10 chip I believe, however my Ubuntu 10.10 is a fresh install and appears to have all the Nouveau drivers pre-installed (which I guess is how i'm typing now ha ha) the only problems seems to be that I need to place your nouveau_vieux_dri.so into my /usr/lib/dri and restart!

I am a complete noob and I mean COMPLETE, so assuming I place your nouveau_vieux_dri.so on my desktop or in my Download folder what would I need to do to get it into the desired destination? I tried drag and drop but Ubuntu wasn't happy with that and threw back my permission as denied!

Please could you give me some incredibly easy/simple step-by-step instructions of how to move that file to the desired destination of /usr/lib/dri ? It would really make my day as i'm pretty sure I have all the other Nouveau already... here is a link to my current post asking for assistance on the subject, in case you need to see my system specs: [http://ubuntuforums.org/showthread.php?t=1605491](http://ubuntuforums.org/showthread.php?t=1605491)

:mrgreen: I Am Noob

---

### Post by christian.remboldt on 2010-10-25
@I Am Noob, Press Alt+F2 this will open the gnome run application window. In this window type "gksu nautilus" and press enter. You then will be prompted to enter you Administration Password. If you enter the password correctly you will open the Nautilus File Manager with root permission. From there you can just browser to the desired directory and drag and drop your file. Be careful using this. Linux is designed around a permission system to prevent people from making changes to files they shouldn't.

Another option is to press "Ctrl+Alt+t" this will open a terminal window. In the terminal type "cd /home/<user name>/Desktop" then hit enter. In place of <user name> make sure to put your user name. This will change you current working directory to the desktop. Then type "sudo cp nouveau_vieux_dri.so /usr/lib/dri" and hit enter. You will be prompted for your administrator password. On successfully entering the password and pressing enter the file will be copied.

---

### Post by I Am Noob on 2010-10-26
Ok.. firstly I would like so send out a **HUGE** thank you to [[COLOR=#d40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104"):KS [John Harrington]("http://ubuntuforums.org/member.php?u=370025"):KS and [christian.remboldt]("http://ubuntuforums.org/member.php?u=1162302"):KS  for their replies and feedback into resolving the issues I have mention  on this thread and two others... nobody forces you to help out of these  forums and your help with me has been **GREATLY** appreciated... Than you :mrgreen:


**My Original Thread:** [http://ubuntuforums.org/showthread.php?t=1605491](http://ubuntuforums.org/showthread.php?t=1605491) 
**[John Harrington]("http://ubuntuforums.org/member.php?u=370025")'s post is in this thread:** [http://ubuntuforums.org/showthread.php?t=1592628](http://ubuntuforums.org/showthread.php?t=1592628)
**[christian.remboldt]("http://ubuntuforums.org/member.php?u=1162302")'s post/thread can be found here:** [http://ubuntuforums.org/showthread.php?t=1590367](http://ubuntuforums.org/showthread.php?t=1590367)


I have not managed to resolve ALL my issues (will ask you another Question at the end of this reply), but here's what I did:

> **cariboo907 said:**
> Nvidia hasn't created a driver for your  graphics card that is compatible with the latest version of Xorg used in  Maverick. The nouveau drivers work quite well on even newer graphics  cards. To get 3D you need to install libgl1-mesa-dri-experimental, it is  in the repositories.

I took this advice and did install libgl1-mesa-dri-experimental from my  repositories within System>Administration>Synaptic Package Manager  but unfortunately this did not solve my issue, I was still unable to  activate Visual Effects within System>Preferences>Appearance after  double checking with a new reboot of course :sad:

Then I re-read this thread: [http://ubuntuforums.org/showthread.php?t=1590367](http://ubuntuforums.org/showthread.php?t=1590367) from [christian.remboldt]("http://ubuntuforums.org/member.php?u=1162302") and decided that because I had a FRESH install I would not need to make changes to /etc/X11/xorg.conf.
as the Nouveau drivers were already installed by default. However I did take the following advice...

> **christian.remboldt said:**
> you need the 3d driver this file is  not included in any package. /usr/lib/dri/nouveau_vieux_dri.so

...but instead building the file myself (because im SUCH a noob) I took a big leap of faith...

> **christian.remboldt said:**
> If you don't want to build it yourself, here is a link to the one I built yesterday. [http://www.mediafire.com/?bzszrsej376y8q7](http://www.mediafire.com/?bzszrsej376y8q7)

and did the unthincable, as a noob, to download and used someone else' self built file!

I then moved my file  to /usr/lib/dri 

> **christian.remboldt said:**
> "Ctrl+Alt+t" this will open a  terminal window. In the terminal type "cd  /home/<user  name>/Desktop" then hit enter. In place of <user  name> make  sure to put your user name. This will change you current  working  directory to the desktop. Then type "sudo cp  nouveau_vieux_dri.so  /usr/lib/dri" and hit enter. You will be prompted  for your  administrator password. On successfully entering the password  and  pressing enter the file will be copied.

and restarted... Sh'bang, Sh'bong Thongsong! I suddenly had my Ubuntu  10.10 singing and dancing, running all the extra Visual Effects quite  nicely :grin:

[B]NOW... the only problem is that Ubuntu still does not recognise my LG M228WA - BZ monitor!
Its a 22" screen and has always run at much higher resolutions than  1024x768, I do realise that my Nvidia graphics card(s) may have had some  role to play in that but im sure this monitor once told me itself (when  I configured Windows resolution wrong) that its best resolution was  something like 1680 x 1050... so my question is HOW do I get Ubuntu to  recognise the true potential of my monitor?[/B] :confused:

[B]PLEASE HELP ME ONCE MORE...

[/B]:mrgreen:I Am Noob

P.S.

> **cariboo907 said:**
> There is a firewall, iptables installed by default, so all you need is a  frontend to set firewall rules. Ufw is installed by default, it stands  for uncomplicated firewall, it is a command line tool for setting  firewall rules. There is also a graphical tool that has the same  function called Gufw, it is in the repositories. To enable the default  rules with ufw, just open a Applications->Accessories->Terminal  and type:
 
 ```
sudo ufw enable
```If you are running a default installation  without any extra services like, ssh, remote desktop or a web server the  default firewall rules are more than enough. If you have an other  computer on your local network, you can do a port scan against the  system to check it for yourself.
 
 I also took this advice and my firewall is now enabled GUI style, thanks again!

---

### Post by christian.remboldt on 2010-10-26
@I Am Noob. Alt+F2; gnome-display-properties.

---

### Post by cratima on 2010-10-28
Hi Christian,

I followed your instructions but the X server crashed with the following errors (see below the relevant sequence from the X log file):

[    87.317] drmOpenDevice: node name is /dev/dri/card0
[    87.317] drmOpenDevice: open result is 8, (OK)
[    87.317] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    87.317] drmOpenDevice: node name is /dev/dri/card0
[    87.317] drmOpenDevice: open result is 8, (OK)
[    87.317] drmOpenByBusid: drmOpenMinor returns 8
[    87.317] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    87.318] (EE) [drm] failed to open device
[    87.318] (EE) No devices detected.

My video card is Nvidia GeForce 3 Ti200.

/dev/dri/card0 exists and the nouveau and related drivers are loaded:
```
[FONT=Courier New]$ ls -la /dev/dri/card0 
crw-rw----+ 1 root video 226, 0 2010-10-28 23:17 /dev/dri/card0[/FONT]
``````
[FONT=Courier New]$ lsmod |grep nouveau
nouveau        517628  0 
ttm             56825  1 nouveau
drm_kms_helper  30200  1 nouveau
drm            168726  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit     5168  1 nouveau[/FONT]

```Any idea?

Thanks.

---

### Post by christian.remboldt on 2010-10-28
@cratima You card appears to only be supported by the oldest legacy driver (71.86.xx). The Nouveau driver should still work, but I'm not sure about Mesa Dri for 3d. If you still cant get nouveau working with out 3d, I'd try xserver-xorg-video-nv instead.

---

### Post by cascade9 on 2010-10-29
> **christian.remboldt said:**
> @cratima You card appears to only be supported by the oldest legacy driver (71.86.xx). The Nouveau driver should still work, but I'm not sure about Mesa Dri for 3d. If you still cant get nouveau working with out 3d, I'd try xserver-xorg-video-nv instead.

Since I've never run a GF3/Ti200/Ti500, I cant know for sure, but if you search for drivers at nvidia, the GF3 series does work with the 96.xx drivers.

---

### Post by cratima on 2010-10-29
> **christian.remboldt said:**
> @cratima You card appears to only be supported by the oldest legacy driver (71.86.xx). The Nouveau driver should still work, but I'm not sure about Mesa Dri for 3d. If you still cant get nouveau working with out 3d, I'd try xserver-xorg-video-nv instead.

I was using nvidia-96.xx before Ubuntu 10.10 and never used 71.86.xx.

Currently I am using xserver-xorg-video-nv but I was looking for Nouveau trying to get 3D acceleration and Compiz working.

Thanks.

---

### Post by dnferro on 2010-10-29
Used rollback suggested by messenjer (tenx!).

Ran autogen.sh. I had to install a number of extra packages:

sudo apt-get install libxdamage-dev libexpat1-dev libxi-dev bison

Got it working now. Tenx! FPS in glxgears up from 6 to 47 FPS ( i know this not a proper benchmarking tool). Is there some 'objective' way of telling it worked?

---

### Post by MonsterTrimble on 2010-11-09
Has anyone had success with the recently released update (9.43.19)? Has it made it into the repos yet?

See info here: [http://www.linux-archive.org/ubuntu-user/447849-nvidia-96-drivers-finally-available-maverick-10-10-a.html](http://www.linux-archive.org/ubuntu-user/447849-nvidia-96-drivers-finally-available-maverick-10-10-a.html)

My laptop is on Lucid still and I really want to get it to Maverick. There are some nice LXDE packages I want to upgrade to.

---

### Post by dnferro on 2010-11-11
@MonsterTrimble

I installed the recently released update (9.43.19)using this link
[http://70.87.46.147/vbulletin/showthread.php?t=156746](http://70.87.46.147/vbulletin/showthread.php?t=156746)
worked fine with me.

---

### Post by MonsterTrimble on 2010-11-17
@dnferro - I added the PPA to my lucid box, updated the driver then ran dist-upgrade. Worked flawlessly.

---

### Post by Oligarf on 2011-01-16
Thanks Christian! Your explanation solved my X trouble. :-)

After upgrading to 10.10 some network drives didn't mount either, so I thought I would have to spend some time on fstab after fixing my graphics. Peculiarly enough the network drives mounted again after applying this fix...

---

### Post by grouchyolddude on 2011-02-15
okay, I'm have issues with the NVIDIA 96 driver. The hardware driver manager says it is installed and enabled, but I'm geting an error > You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
  There is an option in the nvidia x server settings that asks to "include X display names in config file" that box is NOT checked, should it be? 
  > o@o-desktop:~$ sudo nvidia-xconfig
[sudo] password for o: 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


I'm pretty ignorant to all of this. It all actually started just trying to get google earth to work. I'm currently getting the blank screen scenario where the earth map is suppose to appear. 
  I've read through the thread, and I'm not sure if I'm more or less confused. Sorry..

---

### Post by dnferro on 2011-02-24
@grouchyolddude:

Earlier posts basically discuss using newest/experimental driver versions of nvidia (not yet in ubuntu's respository but using a PPA) or the nouveau opensource driver for nvidia cards. 

-what is the nvidia96 driver version you used? 96.43.?
-please provide the contents of your /etc/X11/xorg.conf file.

---

