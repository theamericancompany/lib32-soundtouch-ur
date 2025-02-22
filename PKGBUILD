# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Maintainer: Patrick Northon <northon_patrick3@yahoo.ca>
# Contributor: Nocifer <apmichalopoulos at gmail dot com>
# Contributor: Maxime Gauduin <alucryd@archlinux.org>
# Contributor: josephgbr <rafael.f.f1@gmail.com>

_ml="lib32-"
_pkg=soundtouch
pkgname="${_ml}${_pkg}"
pkgver=2.3.3
_commit="e83424d5928ab8513d2d082779c275765dee31b9"
pkgrel=1
_pkgdesc=(
  'An open-source audio processing library'
  'for changing the tempo, pitch and playback'
  'rates of audio streams or audio files (32 bit)'
)
arch=(
  'x86_64'
)
url="https://www.surina.net/${_pkg}"
license=(
  'LGPL2.1'
)
depends=(
  "${_ml}gcc-libs"
  "${_pkg}"
)
makedepends=(
  'cmake'
  'git'
  'ninja'
)
_http="https://codeberg.org"
_ns="${_pkg}"
_url="${_http}/${_ns}/${_pkg}"
_tag_name="commit"
_tag="${_commit}"
source=(
  "git+${_url}.git#${_tag_name}=${_tag}"
)
sha256sums=(
  '60ed34e8efe81938e6782d78d5ef5ab347a08ff57b47395043853ebeb0eee3ab'
)

build() {
  local \
    _cmake_opts=()
  _cmake_opts=(
    -S
      "${_pkg}"
    -B
      "build"
    -G
      "Ninja"
    -DCMAKE_BUILD_TYPE='Release'
    -DCMAKE_INSTALL_PREFIX="/usr"
    -DBUILD_SHARED_LIBS="ON"
    -DCMAKE_CXX_FLAGS_RELEASE='-m32 -DNDEBUG'
    -DCMAKE_INSTALL_LIBDIR="lib32"
  )
  cd \
    "${srcdir}"
  cmake \
    "${_cmake_opts[@]}"
  cmake \
    --build \
      "build"
}

package() {
  cd \
    "${srcdir}"
  DESTDIR="${pkgdir}" \
  cmake \
    --install \
      "build"
  rm \
    -rf \
    "${pkgdir}/usr/"{"bin","doc","include","share"}
}
