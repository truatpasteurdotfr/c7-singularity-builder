Bootstrap: library
From: tru/default/c7-minimal

%post

yum -y update \
&& \
yum -y install \
	git \
	gcc \
	make \
	libuuid-devel \
	libseccomp-devel \
	openssl-devel \
	rpm-build \
	wget \
&& \
yum -y install epel-release \
&& \
yum -y install \
	golang && \
yum -y clean all

%runscript
if [ $# -ge 1 ]; then
for i in "$@"
do
[ -f singularity-${i}.tar.gz ] || wget  https://github.com/sylabs/singularity/releases/download/v${i}/singularity-${i}.tar.gz -O singularity-${i}.tar.gz \
&& \
rpmbuild -ta singularity-${i}.tar.gz
done
else
echo "usage: $0 singularity_version_to_build_from_released_source"
echo "H=\`mktemp -d /dev/shm/builderXXX\`"
echo "singularity run --home \$H library://tru/default/c7-singularity-builder 3.3.0"
fi
