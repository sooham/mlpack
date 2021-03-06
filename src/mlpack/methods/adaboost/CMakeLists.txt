# Define the files we need to compile.
# Anything not in this list will not be compiled into mlpack.
set(SOURCES
  adaboost.hpp
  adaboost_impl.hpp
  adaboost_model.hpp
  adaboost_model.cpp
)

# Add directory name to sources.
set(DIR_SRCS)
foreach(file ${SOURCES})
  set(DIR_SRCS ${DIR_SRCS} ${CMAKE_CURRENT_SOURCE_DIR}/${file})
endforeach()
# Append sources (with directory name) to list of all mlpack sources (used at
# the parent scope).
set(MLPACK_SRCS ${MLPACK_SRCS} ${DIR_SRCS} PARENT_SCOPE)

add_cli_executable(adaboost)
add_python_binding(adaboost)
add_julia_binding(adaboost)
add_go_binding(adaboost)
add_markdown_docs(adaboost "cli;python;julia;go" "classification")
