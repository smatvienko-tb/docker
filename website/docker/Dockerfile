#
# Copyright © 2016-2020 The Thingsboard Authors
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

FROM ruby:2.7.7

RUN apt-get update \
    && apt-get upgrade --yes \
    && apt-get autoremove --purge --yes \
    && apt-get install -y --no-install-recommends \
        software-properties-common make g++ graphicsmagick-imagemagick-compat\
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && gem install bundler -v 2.1.4 --no-document \
    && gem install ffi -v 1.16.3 --no-document  \
    && gem install public_suffix -v 5.1.1 --no-document \
    && gem list '^jekyll$' --remote --all \
    && gem install jekyll -v 3.9.5 --no-document \
    && gem install nokogiri -v 1.15.5 --no-document \
    && gem install faraday-net_http -v 3.0.2 --no-document \
    && gem install faraday -v 2.8.1 --no-document  \
    && gem install activesupport -v 7.1.4 --no-document \
    && gem list '^github-pages$' --remote --all \
    && gem install github-pages -v 231 --no-document \
    && echo 'done'

WORKDIR /website/

EXPOSE 4000

CMD bundle install && ./restart.sh
