LOCAL_PATH = .
include Common.mk

CPP_FILE_EXTENSION = c
LIBNAME := libpng.a
PREBUILT_DIR = ../jni-prebuilt/linux-x86/
OBJECTS = $(LOCAL_SRC_FILES:%.$(CPP_FILE_EXTENSION)=build/obj/%.o)
C_INCLUDES := $(addprefix -I, $(LOCAL_C_INCLUDES))
CPPFLAGS = $(LOCAL_CFLAGS) $(C_INCLUDES)

target : $(PREBUILT_DIR)/$(LIBNAME)

$(PREBUILT_DIR)/$(LIBNAME) : build/$(LIBNAME) 
	cp build/$(LIBNAME) $(PREBUILT_DIR)/$(LIBNAME) 

build/$(LIBNAME): $(OBJECTS) 
	ar -rf build/$(LIBNAME) $(OBJECTS)
	
build/obj/%.o : %.$(CPP_FILE_EXTENSION) $(LOCAL_C_INCLUDES)
	@mkdir -p `dirname $@`
	$(CXX) -o $@ -c $*.$(CPP_FILE_EXTENSION) $(CPPFLAGS)

clean:
	$(RM) $(OBJECTS) build/$(LIBNAME)