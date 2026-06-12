---
title: "HOW TO INSTALL sq930x.c"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by Dausto on 2008-12-27
Hi,
I'm a newbie, and I've to solve a Creative WebCam problem on Kubuntu Intrepid, installing a C++ file (sq930x.c) but I've not understood how to... :confused:

**This is the first part of the file**:

```

/*  $Id: sq930x.c,v 1.5 2008/05/02 15:09:43 gerard Exp $

   sq930x vidcam  driver Gerard Klaver
*/

/*SANE FLOW DIAGRAM

   - sane_init() : initialize backend, attach vidcams
   . - sane_get_devices() : query list of vidcam devices
   . - sane_open() : open a particular vidcam device
   . . - sane_set_io_mode : set blocking mode
   . . - sane_get_select_fd : get vidcam fd
   . . - sane_get_option_descriptor() : get option information
   . . - sane_control_option() : change option values
   . .
   . . - sane_start() : start image acquisition
   . .   - sane_get_parameters() : returns actual scan parameters
   . .   - sane_read() : read image data (from pipe)
   . .     (sane_read called multiple times; 
   . .      after sane_read returns EOF)
   . .     go back to sane_start() if more frames desired
   . . - sane_cancel() : cancel operation
   . - sane_close() : close opened vidcam device
   - sane_exit() : terminate use of backend
*/
/*--------------------------------------------------------------------------*/

#define BUILD 5			/* 2006/04/14  update 02-05-2008 */
#define BACKEND_NAME sq930x
#define SQ930X_CONFIG_FILE "sq930x.conf"

/* --------------------- SANE INTERNATIONALISATION ------------------------ */

/* must be first include */
#include "../include/sane/config.h"

#include <errno.h>
#include <fcntl.h>
#include <limits.h>
#include <signal.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>

#include "../include/sane/sane.h"
#include "../include/sane/sanei.h"
#include "../include/sane/saneopts.h"
#include "../include/sane/sanei_usb.h"
#include "../include/sane/sanei_debug.h"
#include "../include/sane/sanei_backend.h"
#include "../include/sane/sanei_config.h"
#include "../include/sane/sanei_jpeg.h"
#include "../include/lassert.h"

/* for add-text routine  */
#include <time.h>
#include "../include/font_6x11.h"
/*-----------------------*/

#include "sq930x.h"

#define TIMEOUT 1000

/*--------------------------------------------------------------------------*/
/* Lists of possible scan modes. */
static SANE_String_Const scan_mode_list[] = {
  COLOR_RGB_STR,
  SANE_VALUE_SCAN_MODE_COLOR,
  COLOR_RAW_STR,

  NULL
};


```


Please, will you help me about procedures?

Thank You in advance.

---

