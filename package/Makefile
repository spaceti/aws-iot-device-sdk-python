
VER := 1.4.1
PACKAGE := python-aws-iot-device-sdk_$(VER)-r0.0_arm926ejste.ipk

all: $(PACKAGE)

$(PACKAGE): control.tar.gz data.tar.gz debian-binary
	ar r $(PACKAGE) control.tar.gz data.tar.gz debian-binary

data.tar.gz:
	rm -rf ipk
	cd ..; python setup.py install --root package/ipk --prefix /usr
	cd ipk; tar czvf ../data.tar.gz .



control.tar.gz: control
	tar czvf control.tar.gz control

control: control.in Makefile
	sed 's/@VER@/$(VER)/g' < control.in > control || rm -f control

debian-binary:
	echo 2.0 > debian-binary

clean: FORCE
	rm -f control debian-binary
	rm -f control.tar.gz
	rm -f data.tar.gz
	rm -rf ipk
#	rm -f python-aws-iot-device-sdk_*.ipk
	rm -f $(PACKAGE)
	rm -rf ../build

FORCE:
