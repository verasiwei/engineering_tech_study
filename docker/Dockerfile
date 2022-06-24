FROM tiagopeixoto/graph-tool
FROM nstrayer/graph-tool-extra:basic-config

# Set maintainer
LABEL description = "graph-tool and some other python packages used for biSBM work" 
LABEL maintainer = "Siwei Zhang" 

# Set the make package user to have a random uid to avoid conflicts
RUN usermod -u 8888 mkpkg
RUN usermod -u 8889 user

# Modify the default user (creatively named 'user') to have the same UID as the person building image
# Add a new user with desired permissions
ARG UID=1000

# Make a new user so we can give custom UID
RUN useradd -ms /bin/bash analysis

# Set userid to some crazy value so we can modify it even if it's already what we need
RUN echo "Building user id is $UID"

# Now set userid to match the user id of the builder of the image
RUN usermod -u $UID analysis

# Define working directory
USER analysis
WORKDIR /home/analysis

# Copy the neccesary scripts into the docker container
ADD bisbm_sim.py /home/analysis/bisbm_sim.py


