---
title: "Ubuntu 12.04 - glib_genmarshal : Cannot execute binary file"
date: 2013-06-10
forum: Hardware
---

### Post by Carlos5 on 2013-06-10
Dear,

Im very new in Ubuntu, Im trying to compile a cross compile with buildroot 2010.02 and Ive this error:



                swfdec.h swfdec_as_array.h swfdec_as_context.h swfdec_as_debugger.h swfdec_as_frame.h swfdec_as_function.h swfdec_as_native_function.h swfdec_as_object.h swfdec_as_types.h swfdec_audio.h swfdec_buffer.h swfdec_file_loader.h swfdec_gc_object.h swfdec_keys.h swfdec_loader.h swfdec_player.h swfdec_player_scripting.h swfdec_rectangle.h swfdec_renderer.h swfdec_script.h swfdec_socket.h swfdec_stream.h swfdec_system.h swfdec_url.h ) > xgen-sec \
        && (cmp -s xgen-sec swfdec_enums.c || cp xgen-sec swfdec_enums.c ) \
        && rm -f xgen-sec
( cd . && glib-mkenums \
                        --fhead "#ifndef __SWFDEC_ENUMS_H__\n#define __SWFDEC_ENUMS_H__\n\n#include <glib-object.h>\n\nG_BEGIN_DECLS\n" \
                        --fprod "/* enumerations from \"@filename@\" */\n" \
                        --vhead "GType @enum_name@_get_type (void) G_GNUC_CONST;\n#define SWFDEC_TYPE_@ENUMSHORT@ (@enum_name@_get_type())\n" \
                        --ftail "G_END_DECLS\n\n#endif /* __SWFDEC_ENUMS_H__ */" \
                swfdec.h swfdec_as_array.h swfdec_as_context.h swfdec_as_debugger.h swfdec_as_frame.h swfdec_as_function.h swfdec_as_native_function.h swfdec_as_object.h swfdec_as_types.h swfdec_audio.h swfdec_buffer.h swfdec_file_loader.h swfdec_gc_object.h swfdec_keys.h swfdec_loader.h swfdec_player.h swfdec_player_scripting.h swfdec_rectangle.h swfdec_renderer.h swfdec_script.h swfdec_socket.h swfdec_stream.h swfdec_system.h swfdec_url.h ) >> xgen-seh \
        && (cmp -s xgen-seh swfdec_enums.h || cp xgen-seh swfdec_enums.h ) \
        && rm -f xgen-seh
glib-genmarshal --prefix=swfdec_marshal ./swfdec_marshal.list --header >> xgen-smh \
        && (cmp -s xgen-smh swfdec_marshal.h || cp xgen-smh swfdec_marshal.h) \
        && rm -f xgen-smh
/bin/bash: /home/carlos/buildroot-2010.02/output/staging/usr/bin/glib-genmarshal: cannot execute binary file
make[2]: *** [swfdec_marshal.h] Error 126
make[2]: Leaving directory `/home/carlos/buildroot-2010.02/output/build/swfdec-0.8.4/swfdec'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/carlos/buildroot-2010.02/output/build/swfdec-0.8.4'
make: *** [/home/carlos/buildroot-2010.02/output/build/swfdec-0.8.4/.stamp_staging_installed] Error 2
 
If I execute /usr/bin glib-genmarshall I receive the same error.
 


Any suggestion¿?  



Thanks you very much.

---

